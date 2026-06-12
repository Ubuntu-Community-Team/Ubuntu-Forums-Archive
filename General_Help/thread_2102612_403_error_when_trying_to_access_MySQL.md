---
title: "403 error when trying to access MySQL"
date: 2013-01-07
forum: General Help
---

### Post by Rhodoferax on 2013-01-07
I'm using Ubuntu Desktop 12.10. Recently, I downloaded and set up Apache2, PHP, and MySQL, using the normal commands:

```
sudo apt-get install apache2
sudo apt-get install php5
sudo apt-get install mysql-client
sudo apt-get install mysql-server
```localhost is set up to be /var/www . I have some HTML and CSS pages in there for a website I'm building for a friend, and they work flawlessly.

I'm using a copy of *PHP and MySQL for Dummies* to teach myself about this arrangement, which directs me to use a couple of PHP files to check everything is working right.

Firstly, I ran [this script]("http://www.janetvalade.com/Programs/phpfd4/ch02/test.phps") to test if PHP was configured correctly; it worked fine.

Then, I ran [ this one]("http://www.janetvalade.com/Programs/phpfd4/ch02/mysql_test.phps") to check if MySQL was working; when I entered localhost/mysql_test.phps into the URL bar, I got a 403 error message:

```
**Forbidden**

 You don't have permission to access /mysql_test.phps on this server.
  Apache/2.2.22 (Ubuntu) Server at 127.0.0.1 Port 80
```This is with the value of $host set to "localhost" and $user set to "root". I didn't set a password for root, so $password is just set to "".

I've tried Googling, but so far I've come up zilch. I've seen a few comments about needing to open port 80, but a) I have no idea how to do that, and b) I don't think that should be an issue when trying to access a page on my own machine.

Does anybody have any idea what might possibly be going wrong?

---

