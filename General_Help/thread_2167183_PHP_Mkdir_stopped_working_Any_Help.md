---
title: "PHP Mkdir stopped working? Any Help?"
date: 2013-08-12
forum: General Help
---

### Post by miklo2 on 2013-08-12
Hello everyone!

I was trying to create a folder using a php file in my /var/www folder. It was working file all the day, but after I changed the permission to my secondary user using the "sudo chown user1:user -R /var/www".... then my phpfile stopped working and didnt create the folders I wanted to create.

I tried so many other ways, but that didnt work either! I do have ALL permissions set for my "user1" which is the other user.

Below is 3 differentt PHP Files that I used and was working fine befor.....

[PHP]
PHP Code 1:
<?php
mkdir("var/www/test", 0755, true)) chmod("var/www/test", 0755);
?>

PHP Code 2:
<?php
mkdir("var/www/test", 0755) 
?>

PHP Code 3:
<?php
mkdir("test", 0777);
?>
[/PHP]

And these are the Permission that I used for change:
```
sudo chown user1:user1 -R /var/www
```

And then tried:
```
sudo chmod u+w  .
```

But It still didnt work.....  I even tried to change everything back to root. Still no folder was created!

Here is my latest permission set with root:
```
drwxrwxr-x  2 user1 user1 4096 Aug 12 20:40 .
drwxr-xr-x 13 root    root     4096 Aug  4 15:19 ..
-rw-r--r--  1 user1 user1  354 Aug 12 20:05 db_connect.php
-rw-r--r--  1 user1 user1   77 Aug 12 20:46 folder.php
-rw-r--r--  1 user1 user1 4102 Aug 12 18:52 report.php
-rw-r--r--  1 user1 user1 2505 Aug 12 18:52 tracker.php
-rw-r--r--  1 user1 user1   45 Aug 12 18:52 session_end.php
```


I really hope I can get some help with this, because I am lost now! I have 2-3 other websites, and I tried the same php file overthere, and it was working fine! So what could be wrong here...?

Thank you very much in advance

---

### Post by Cheesemill on 2013-08-12
Since you changed the permissions your /var/www directory isn't writeable by www-data (the user that Apache runs as).

---

### Post by miklo2 on 2013-08-12
Thanks for the reply, But how can I fix it?

 I am pretty new using Ubuntu,, I have forgot how to add my usergroup to www-data...

---

