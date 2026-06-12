---
title: "help w/ emailing a log file"
date: 2007-07-09
forum: General Help
---

### Post by afbase on 2007-07-09
How can I email myself a log file (/var/log/boot) so I can post my problem to this forum in CLI?

I don't have the mail command, nor uuencode.  If i absolutely need those two commands can somebody show me how to install them.

---

### Post by lisati on 2007-07-09
If you have evolution (or similar) setup for your email you can right-click on the file from a browser and then click on "sent to"

---

### Post by afbase on 2007-07-09
i don't have evolution or a gui, it is a edgy eft LAMP server with no GUI.  Command Line is the only way to do this.  I can't even install a GUI because of this problem.

---

### Post by EndPerform on 2007-07-09
Why not copy the file down to your local machine?  For example, say your server is named webserver and your box is named, well, yourbox.  You could do this:

```
scp webserver:/var/log/boot /home/user/boot.log
``` 

That will perform a secure copy over SSH and pull the file down as /home/user/boot.log on your desktop, then you can email it or do what you like.

---

### Post by afbase on 2007-07-09
I can't ssh to my server.  I got an idea from what you said.  I copied the log files to a place where i could download them.   The BIG problem is this:

> 
$ chmod 777 /var/www/boot
Segmentation Fault


---

### Post by afbase on 2007-07-09
I fear that this "segmentation fault" maybe result to a problem i had [last week]("http://ubuntuforums.org/showthread.php?t=491281").  

Since then, I reinstalled from dapper to edgy.  The only thing that was on that hard drive that was important was my MYSQL db.  I backed up the database and now after the reinstallation, things were smooth until i hit this problem with services not starting, such as mysql, and SSH-server. 

 I'm pretty sure that the /etc/init.d/rcS  is at fault because it keeps giving me errors.  So now I'm trying to obtain a copy of the boot log to show you guys my problem, because that too is a "segmentation fault" error.  Can somebody please help!!!

---

### Post by marsbt on 2007-07-09
You can install sendmail using 
> sudo aptitude install sendmail 
and then use it from commandline to send yourself an email. You can either check man page for sendmail for the usage or search the net for examples.

---

### Post by afbase on 2007-07-11
I already have sendmail installed.  Would anybody know how to send a file (/var/log/boot) by email usuing sendmail?

I made a tiny php script to send the file but no luck so far as to why it won't work.  I placed the php file in /var/log.

```


<?php
$messeage = file_get_contents("boot");
$to = "emailaddress@gmail.com";
mail($to,"test",$message);

?>

```

---

### Post by Mr. C. on 2007-07-11
```
sendmail user@domain.com < file_to_send
```

MrC

---

