---
title: "Again with Apache2, PHP4 &amp; Internal Server Error"
date: 2005-07-08
forum: General Help
---

### Post by hadelikaruna on 2005-07-08
Hello, 

I am newbie with ubuntu. I have just installed Apache2 and PHP4 engine. Firstly, after the installation, I faced the problem that my Apache2 engine didn't want to execute my php file, it kept downloading the file. However, that problem was solved now. Thanks for the discussion in this forum. NOW, I have another problem, my Apache2 engine can only execute file with name index.php, if I ask it to execute testphp.php which contains phpinfo command, I got this error message:
---
[I]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.[/I]
---
However, if the same code is written in index.php, it works perfectly. This is the content of my index.php and testphp.php. Both have the same content. 

---
[I]<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
  <meta content="text/html; charset=ISO-8859-1"
 http-equiv="content-type">
  <title>index.php</title>
</head>
<body>
Old website was down due to harddisk crash. New website is currently in
design. <br>
<br>
You are accessing this website using :
<?php echo $_SERVER['HTTP_USER_AGENT'];
phpinfo();
?>
</body>
</html>[/I]
---
This is the content of my httpd.conf

---
[I]# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
AddType application/x-httpd-php .php[/I]
---
and this is the content of my php4.load
---
*LoadModule php4_module /usr/lib/apache2/modules/libphp4.so*
---

Does anyone has any idea how can I solve this problem ? Where can I view the server error log?  Thank you very much in advance. 

regs, 

hadeli

---

### Post by mrcbrown on 2005-07-08
> **hadelikaruna]Hello, 

I am newbie with ubuntu. I have just installed Apache2 and PHP4 engine. Firstly, after the installation, I faced the problem that my Apache2 engine didn't want to execute my php file, it kept downloading the file. However, that problem was solved now. Thanks for the discussion in this forum. NOW, I have another problem, my Apache2 engine can only execute file with name index.php, if I ask it to execute testphp.php which contains phpinfo command, I got this error message:
---
[I]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.[/I]
---
However, if the same code is written in index.php, it works perfectly. This is the content of my index.php and testphp.php. Both have the same content. 

---
[I]<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
  <meta content="text/html said:**
> ;
phpinfo();
?>
</body>
</html>[/I]
---
This is the content of my httpd.conf

---
[I]# This is here for backwards compatability reasons and to support
#  installing 3rd party modules directly via apxs2, rather than
#  through the /etc/apache2/mods-{available,enabled} mechanism.
#
#LoadModule mod_placeholder /usr/lib/apache2/modules/mod_placeholder.so
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
AddType application/x-httpd-php .php[/I]
---
and this is the content of my php4.load
---
*LoadModule php4_module /usr/lib/apache2/modules/libphp4.so*
---

Does anyone has any idea how can I solve this problem ? Where can I view the server error log?  Thank you very much in advance. 

regs, 

hadeli
 How did you go about installing Apache? Some common areas to check for the log are:

/usr/local/apache/logs/
/www/logs/
/var/log/httpd/

Can you view normal HTML when you goto your site? If not try chmod'ing your home dir "/home/username/" to 701 and your public_html folder to 755 if your using your homedir as a virtual host.

If your log doesn't come up with anything, post a URL example & apache conf, sure I could probably help poke at it some.

---

### Post by hadelikaruna on 2005-07-08
Hello, 

Thanks for the prompt answer, I got this message in my error_log
"Premature end of script headers:testphp.php"

I can also view my html page. The strange thing was my engine could executed index.php, but not another name. 

Currently, I will start the apache2, php4 all over again. I will come to you when I have problems. 

Thanks.

---

