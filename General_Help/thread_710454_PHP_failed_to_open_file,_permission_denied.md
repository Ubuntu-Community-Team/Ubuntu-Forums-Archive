---
title: "PHP failed to open file, permission denied"
date: 2008-02-28
forum: General Help
---

### Post by Arenlor on 2008-02-28
I'm sure that this is just a settings thing but I'm not sure what to set, it's not a webserver it's just my local copy of LAMP on my laptop, anyone able to help me?

---

### Post by astrotech226 on 2008-02-28
This is probably just a simple permissions problem.  Where is the PHP file stored?  And can you show us the results of this?

```
ls -l /path/to/your/phpfile.php
```

Obviously change the path and file name.

---

### Post by Arenlor on 2008-02-28
I have /var/www/arenlor as a symbolic link to /home/arenlor/ftp/arenlor
> -rw-r--r-- 1 arenlor arenlor 1053 2008-02-28 14:32 /var/www/arenlor/test_login/register.php

---

### Post by astrotech226 on 2008-02-28
> **Arenlor said:**
> I have /var/www/arenlor as a symbolic link to /home/arenlor/ftp/arenlor

What does this output?
```

ls -l /home
```

If you get drwxr-x---, that's the problem.  Apache can't get inside your home directory.

---

### Post by Arenlor on 2008-02-28
> drwxr-xr-x 71 arenlor arenlor  4096 2008-02-28 14:47 arenlor It would appear to be that problem, so how do I fix it?

---

### Post by astrotech226 on 2008-02-28
No...  That should be OK.  Let's check the other directories in the path:

```
ls -l /home/arenlor
ls -l /home/arenlor/ftp
ls -l /home/arenlor/ftp/arenlor
```

---

### Post by Arenlor on 2008-02-28
> drwxr-xr-x 5 arenlor arenlor   4096 2008-02-23 02:04 ftp
drwxr-xr-x 11 arenlor arenlor 4096 2008-02-27 16:55 arenlor
drwxrwxrwx 2 arenlor arenlor 4096 2008-02-28 14:29 test_login
I had chmod test_login to see if it'd work, so that's why it's like that.

---

### Post by astrotech226 on 2008-02-28
This actually looks OK.  Let's try this.  Are you running Apache from the Ubuntu packages?  If so go through these steps and let's see where it breaks:
```

sudo su - www-data
cd /home
cd arenlor
cd ftp
cd arenlor
cd test_login
php register.php
```

---

### Post by Arenlor on 2008-02-28
it breaks on the file itself.
> <?php $file = "users.txt";
$fe = fopen($file, 'a') or die("Can't open file for writing.");
$data = "Arenlor::md5('pass')";
fwrite($fe, $data);
fclose($fe);?>
users.txt does exist and is blank. I know about security etc with a text file, but this is just the beginning of a test of an idea.

---

### Post by astrotech226 on 2008-02-28
> **Arenlor said:**
> users.txt does exist and is blank. I know about security etc with a text file, but this is just the beginning of a test of an idea.

So the PHP file runs, but you are now getting a PHP error?  Just for giggles, change this line:

```
$file = "/tmp/users.txt";
```

---

### Post by Arenlor on 2008-02-28
Yeah that worked, odd, what could it be?

---

### Post by astrotech226 on 2008-02-28
I don't know.  I just set up a test environment the same way you do and this is working for me as is.

The only requirement was the test_login directory needed write permission for "other" and it worked.  And you already have that set correctly.  So I'm not sure what else to say.

Just to verify, you are getting this error from the web page when you try to access it at [http://localhost?](http://localhost?)

---

### Post by Arenlor on 2008-02-28
Yep, [http://localhost/arenlor/test_login/register.php](http://localhost/arenlor/test_login/register.php)
> Warning: fopen(users.txt) [function.fopen]: failed to open stream: Permission denied in /home/arenlor/ftp/arenlor/test_login/register.php on line 12
Can't open file for writing
Don't think I gave the actual error yet.
EDIT: Also I can't move files (file uploading)

---

### Post by astrotech226 on 2008-02-28
> **Arenlor said:**
> Yep, [http://localhost/arenlor/test_login/register.php](http://localhost/arenlor/test_login/register.php)

Don't think I gave the actual error yet.
EDIT: Also I can't move files (file uploading)

What happens if you:

```
mkdir /home/arenlor/ftp/arenlor/test_login/tmp
chown www-data /home/arenlor/ftp/arenlor/test_login/tmp
chmod 640 /home/arenlor/ftp/arenlor/test_login/tmp
```

Change your line in the php file:

```
$file = "./tmp/users.txt";
```

Notice the addition of the dot in front of "/tmp".  And then try it again.  This will make this a little more secure than giving everyone write permission to where your scripts are going to be.

---

### Post by Arenlor on 2008-02-28
Same issue, but when I try to access [http://localhost/arenlor/test_login/tmp/](http://localhost/arenlor/test_login/tmp/) I get a 403 Forbidden
Maybe I screwed up in chowing it.

> arenlor@arenlor:~$ chown www-data /home/arenlor/ftp/arenlor/test_login/tmp
chown: changing ownership of `/home/arenlor/ftp/arenlor/test_login/tmp': Operation not permitted
arenlor@arenlor:~$ sudo chown www-data /home/arenlor/ftp/arenlor/test_login/tmp
[sudo] password for arenlor:
arenlor@arenlor:~$ sudo chmod 640 /home/arenlor/ftp/arenlor/test_login/tmp

---

### Post by astrotech226 on 2008-02-28
Nevermind. I screwed that all up.  It's this:

```
sudo chmod 755 /home/arenlor/ftp/arenlor/test_login/tmp
```

---

### Post by Arenlor on 2008-02-28
That works, but why doesn't it work in my root directory?

---

### Post by astrotech226 on 2008-02-28
> That works, but why doesn't it work in my root directory?

It should have.  All it takes is one little thing out of whack and it won't work correctly.

Are you doing some testing now or are you putting this into production?  Because there are easier ways to do this sort of thing with the correct user/group and permissions setup.  Especially if more than one user is going to be developing or uploading files.

Let us know if you want help with that.

---

### Post by Arenlor on 2008-02-28
I'm doing testing before I put it out into production, basically I'm trying to make a system which will let people use PHP without a MySQL Database being needed (or any database)

---

