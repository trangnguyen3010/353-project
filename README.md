## Overview
A simple web application for organization management. This is a project for CMPT 353 (Fullstack Development).
It uses:
- https
- sessions (for login and logout)
- node-cron (for database backup)
- bcrypt (for hasing passwords)

## Functionalities
* Sign-up/Login/Logout
* Register/Update/Delete customers
* Register/Update/Delete staff (only manager accounts are given this functionality)
* Create/Show/Sort reports of a customer

## Technologies
* Docker
* Javascript, Embedded Javascript
* MySQL
* HTML
* CSS
* Bootstrap

## Launch
Open 2 terminals:

#### 1st terminal:
csh ./run.csh\
npm start

#### 2nd terminal:
docker exec -it db1 /bin/bash\
mysql -uroot -padmin\
use project\
CREATE TABLE `users` (   `id` int(10) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
                          `firstName` varchar(255) DEFAULT NULL,
                           `lastName` varchar(255) DEFAULT NULL,
                           `phoneNumber` varchar(255) DEFAULT NULL,
                           `location` varchar(50) DEFAULT NULL ) ENGINE=InnoDB DEFAULT CHARSET=latin1;

CREATE TABLE `roles` (   `id` int(10) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
                          `roleName` varchar(255) DEFAULT NULL,
                           `roleDescription` text(5000) DEFAULT NULL ) ENGINE=InnoDB DEFAULT CHARSET=latin1;

INSERT INTO roles (roleName, roleDescription) VALUES ('Manager', 'Can register/update/delete staffs and register/update/delete customers');
INSERT INTO roles (roleName, roleDescription) VALUES ('Staff', 'Can register/update/delete customers');

CREATE TABLE `staffs` (   `id` int(10) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
                            `username` varchar(50) NOT NULL,
                            `password` varchar(255) NOT NULL,
                          `roleID` int(10) UNSIGNED,
                          `firstName` varchar(255) DEFAULT NULL,
                           `lastName` varchar(255) DEFAULT NULL,
                           `phoneNumber` varchar(255) DEFAULT NULL),
                           <!-- FOREIGN KEY (roleID) REFERENCES roles(id) ) ENGINE=InnoDB DEFAULT CHARSET=latin1;


INSERT INTO `staffs` (username, password, roleID, firstName, lastName, phoneNumber) VALUES ('test', 'test', 1, 'trang', 'nguyen', '2424242');
INSERT INTO `staffs` (username, password, roleID, firstName, lastName, phoneNumber) VALUES ('trang', '30102001', 2, 'trang', 'nguyen', '2424242');


CREATE TABLE reports ( `id` int(10) UNSIGNED PRIMARY KEY NOT NULL AUTO_INCREMENT,
                          `userID` int(10) UNSIGNED,
                          topic VARCHAR(255) NOT NULL,
                           data TEXT(65535) NOT NULL,
                        timestamp DATETIME NOT NULL);

