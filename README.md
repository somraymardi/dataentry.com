# dataentry.com
CREDIT BY THE SOMRAY
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Data Entry</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/css/bootstrap.min.css">
    <style>
        body {
            background-color: #f0f0f0;
        }
        .container {
            max-width: 800px;
            margin-top: 50px;
            padding: 20px;
            background-color: #ffffff;
            border: 1px solid #dddddd;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
        #data-entry-form {
            display: none;
        }
        #entered-data {
            display: none;
        }
        .photo-container {
            width: 100px;
            height: 100px;
            border: 1px solid #ddd;
            border-radius: 10px;
            padding: 5px;
        }
        .photo-container img {
            width: 100%;
            height: 100%;
            object-fit: cover;
        }
        #login-history {
            display: none;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Data Entry</h1>
        <button class="btn btn-primary" data-toggle="modal" data-target="#login-modal" id="login-button">Login/Signup</button>
        <button class="btn btn-secondary" id="logout-btn" style="display: none;">Logout</button>
        <button class="btn btn-secondary" id="login-history-btn" style="display: none;">Login History</button>
        <hr>
        <form id="data-entry-form">
            <div class="form-group">
                <label for="name">Name:</label>
                <input type="text" class="form-control" id="name" required>
            </div>
            <div class="form-group">
                <label for="email">Email:</label>
                <input type="email" class="form-control" id="email" required>
            </div>
            <div class="form-group">
                <label for="phone">Phone Number:</label>
                <input type="tel" class="form-control" id="phone" required>
            </div>
            <div class="form-group">
                <label for="address">Address:</label>
                <input type="text" class="form-control" id="address" required>
            </div>
            <div class="form-group">
                <label for="photo">Photo:</label>
                <input type="file" class="form-control" id="photo" accept="image/*">
                <div class="photo-container">
                    <img id="photo-preview" src="" alt="Photo Preview">
                </div>
            </div>
            <button type="submit" class="btn btn-primary" id="submit-btn" disabled>Submit</button>
        </form>
        <hr>
        <div id="entered-data">
            <h2>Entered Data:</h2>
            <table id="data-table" class="table table-striped">
                <thead>
                    <tr>
                        <th>Name</th>
                        <th>Email</th>
                        <th>Phone Number</th>
                        <th>Address</th>
                        <th>Photo</th>
                    </tr>
                </thead>
                <tbody id="data-table-body">
                </tbody>
            </table>
        </div>
        <div id="login-history">
            <h2>Login History:</h2>
            <table id="login-history-table" class="table table-striped">
                <thead>
                    <tr>
                        <th>Date</th>
                        <th>Email</th>
                    </tr>
                </thead>
                <tbody id="login-history-body">
                </tbody>
            </table>
        </div>
        <p id="login-success" style="display: none; color: green;"></p>
        <p id="logout-success" style="display: none; color: green;"></p>
    </div>

    <!-- Modal -->
    <div class="modal fade" id="login-modal" tabindex="-1" role="dialog" aria-labelledby="login-modal-label" aria-hidden="true">
        <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title" id="login-modal-label">Login/Signup</h5>
                    <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                        <span aria-hidden="true">&times;</span>
                    </button>
                </div>
                <div class="modal-body">
                    <ul class="nav nav-tabs" id="myTab" role="tablist">
                        <li class="nav-item" role="presentation">
                            <a class="nav-link active" id="login-tab" data-toggle="tab" href="#login" role="tab" aria-controls="login" aria-selected="true">Login</a>
                        </li>
                        <li class="nav-item" role="presentation">
                            <a class="nav-link" id="signup-tab" data-toggle="tab" href="#signup" role="tab" aria-controls="signup" aria-selected="false">Signup</a>
                        </li>
                    </ul>
                    <div class="tab-content" id="myTabContent">
                        <div class="tab-pane fade show active" id="login" role="tabpanel" aria-labelledby="login-tab">
                            <form id="login-form">
                                <div class="form-group">
                                    <label for="login-email">Email:</label>
                                    <input type="email" class="form-control" id="login-email" required>
                                </div>
                                <div class="form-group">
                                    <label for="login-password">Password:</label>
                                    <input type="password" class="form-control" id="login-password" required>
                                </div>
                                <button type="submit" class="btn btn-primary">Login</button>
                            </form>
                        </div>
                        <div class="tab-pane fade" id="signup" role="tabpanel" aria-labelledby="signup-tab">
                            <form id="signup-form">
                                <div class="form-group">
                                    <label for="signup-name">Name:</label>
                                    <input type="text" class="form-control" id="signup-name" required>
                                </div>
                                <div class="form-group">
                                    <label for="signup-email">Email:</label>
                                    <input type="email" class="form-control" id="signup-email" required>
                                </div>
                                <div class="form-group">
                                    <label for="signup-password">Password:</label>
                                    <input type="password" class="form-control" id="signup-password" required>
                                </div>
                                <div class="form-group">
                                    <label for="signup-confirm-password">Confirm Password:</label>
                                    <input type="password" class="form-control" id="signup-confirm-password" required>
                                </div>
                                <button type="submit" class="btn btn-primary">Signup</button>
                                <p id="signup-success" style="display: none; color: green;">Signup successful!</p>
                                <p id="password-mismatch" style="display: none; color: red;">Passwords do not match!</p>
                                <p id="email-exists" style="display: none; color: red;">Email already exists!</p>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://code.jquery.com/jquery-3.2.1.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.0.0/js/bootstrap.min.js"></script>
    <script>
        let data = JSON.parse(localStorage.getItem('data')) || [];
        let users = JSON.parse(localStorage.getItem('users')) || [];
        let loginHistory = JSON.parse(localStorage.getItem('loginHistory')) || [];

        $(document).ready(function() {
            checkLoginStatus();
        });

        function checkLoginStatus() {
            let user = JSON.parse(localStorage.getItem('loggedInUser'));
            if (user) {
                $('#data-entry-form').show();
                $('#submit-btn').prop('disabled', false);
                $('#logout-btn').show();
                $('#login-button').hide();
                $('#login-history-btn').show();
                updateLoginHistory();
                showEnteredData();
                $('#entered-data').show();
            } else {
                $('#login-button').show();
                $('#logout-btn').hide();
                $('#data-entry-form').hide();
                $('#submit-btn').prop('disabled', true);
                $('#entered-data').hide();
                $('#login-history-btn').hide();
                $('#login-history').hide();
            }
        }

        function showEnteredData() {
            let html = '';
            data.forEach(function(entry) {
                html += '<tr><td>' + entry.name + '</td><td>' + entry.email + '</td><td>' + entry.phone + '</td><td>' + entry.address + '</td><td><img src="' + entry.photo + '" alt="Photo" width="50" height="50"></td></tr>';
            });
            $('#data-table-body').empty();
            $('#data-table-body').append(html);
        }

        $('#login-form').submit(function(event) {
            event.preventDefault();
            let email = $('#login-email').val();
            let password = $('#login-password').val();
            let user = users.find(u => u.email === email && u.password === password);
            if (user) {
                localStorage.setItem('loggedInUser', JSON.stringify(user));
                loginHistory.push({ email: email, date: new Date().toLocaleString() });
                localStorage.setItem('loginHistory', JSON.stringify(loginHistory));
                checkLoginStatus();
                $('#login-modal').modal('hide');
                $('#login-success').text('Login successful!');
                $('#login-success').show();
                setTimeout(function() {
                    $('#login-success').hide();
                }, 2000);
            } else {
            }
        });

        $('#signup-form').submit(function(event) {
            event.preventDefault();
            let name = $('#signup-name').val();
            let email = $('#signup-email').val();
            let password = $('#signup-password').val();
            let confirmPassword = $('#signup-confirm-password').val();
            let user = users.find(u => u.email === email);
            if (user) {
                $('#email-exists').show();
                $('#password-mismatch').hide();
                $('#signup-success').hide();
            } else if (password === confirmPassword) {
                users.push({ name, email, password });
                localStorage.setItem('users', JSON.stringify(users));
                localStorage.setItem('loggedInUser', JSON.stringify({ name, email, password }));
                loginHistory.push({ email: email, date: new Date().toLocaleString() });
                localStorage.setItem('loginHistory', JSON.stringify(loginHistory));
                checkLoginStatus();
                $('#login-modal').modal('hide');
                $('#signup-success').show();
                $('#password-mismatch').hide();
                $('#email-exists').hide();
            } else {
                $('#password-mismatch').show();
                $('#signup-success').hide();
                $('#email-exists').hide();
            }
        });

        $('#logout-btn').click(function() {
            localStorage.removeItem('loggedInUser');
            checkLoginStatus();
            $('#logout-success').text('Logout successful!');
            $('#logout-success').show();
            setTimeout(function() {
                $('#logout-success').hide();
            }, 2000);
        });

        function updateLoginHistory() {
            let html = '';
            loginHistory.forEach(function(login) {
                html += '<tr><td>' + login.date + '</td><td>' + login.email + '</td></tr>';
            });
            $('#login-history-body').empty();
            $('#login-history-body').append(html);
        }

        $('#login-history-btn').click(function() {
            if ($('#login-history').is(':visible')) {
                $('#login-history').hide();
            } else {
                updateLoginHistory();
                $('#login-history').show();
            }
        });

        $('#photo').on('change', function() {
            let file = this.files[0];
            let reader = new FileReader();
            reader.onload = function(event) {
                $('#photo-preview').attr('src', event.target.result);
            };
            reader.readAsDataURL(file);
        });

        $('#data-entry-form').submit(function(event) {
            event.preventDefault();
            let name = $('#name').val();
            let email = $('#email').val();
            let phone = $('#phone').val();
            let address = $('#address').val();
            let photo = $('#photo')[0].files[0];
            let photoData = null;
            if (photo) {
                let reader = new FileReader();
                reader.onload = function(event) {
                    photoData = event.target.result;
                    data.push({ name, email, phone, address, photo: photoData });
                    localStorage.setItem('data', JSON.stringify(data));
                    showEnteredData();
                };
                reader.readAsDataURL(photo);
            } else {
                data.push({ name, email, phone, address, photo: '' });
                localStorage.setItem('data', JSON.stringify(data));
                showEnteredData();
            }
        });
    </script>
</body>
</html>
