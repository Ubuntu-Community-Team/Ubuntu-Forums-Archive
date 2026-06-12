---
title: "mysql_connect() undefined function?"
date: 2007-06-02
forum: General Help
---

### Post by T3h_Dohtem on 2007-06-02
Im getting this error: 
Fatal error: Call to undefined function mysql_connect()
I don't know what the cause is, Ive installed the php5-mysql package. Is there something else I'm forgetting? Ive already been able to run mysql php scripts on a different ubuntu server I have. mysql_connect() should be built in, correct?

Thanks for any help!

---

### Post by CanadianDSM on 2007-06-02
Are you sure you have the syntax correct in your PHP? I've made the switch to mysqli (php5-mysqli). You should give it a try!

Example:

mysql_connect($dbhost,$dbuser,$dbpass);
@mysql_select_db($dbname) or die( "Unable to select database");

Can you connect to the database from the MySQL console?

---

### Post by CrucifiedEgo on 2007-06-02
> **T3h_Dohtem said:**
> Im getting this error: 
Fatal error: Call to undefined function mysql_connect()
I don't know what the cause is, Ive installed the php5-mysql package. Is there something else I'm forgetting? Ive already been able to run mysql php scripts on a different ubuntu server I have. mysql_connect() should be built in, correct?

Thanks for any help!

Did you restart your webserver after installing php5-mysql?  Does phpinfo() show mysql available?  One of those two should give you your answer.

-J

---

### Post by madhumohan on 2007-06-06
Hi,
    I m getting the same error, i installed php5-mysql and i restarted web server as well. I m able to connect to mysql from bash. php is also running fine. but getting error like 'undefined function mysql_connect()'....and i m not getting error if i run from prompt like:

root@ubuntu # php abc.php
1 madhu

Please help.

Thanks
Madhu

---

### Post by soulscreme on 2007-07-01
Any chance that this has been solved?  I've been toying with this for a few days now and haven't been able to fix it.  I'm using Apache2 and PHP5.  If I run the PHP from the command line it works perfectly.  Inside of the browser it gives me this error.  I'm pretty stumped.

---

### Post by madhumohan on 2007-07-02
Just modify PHP.ini file, uncomment mysql.so entry...and place the directory path of mysql.so file.

u can find the location of mysql.so file by typing the command:
locate mysql.so

Enjoy....Its working

---

### Post by dzark on 2007-07-18
I just had the same problem, and uncommenting the line didn't work..

After closer inspection, the line in my php.ini read:

extension=msql.so

Took me a while to see that the "y" was missing.... Strange...

cheers,
dzark

---

