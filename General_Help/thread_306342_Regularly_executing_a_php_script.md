---
title: "Regularly executing a php script"
date: 2006-11-24
forum: General Help
---

### Post by roflcopter_1 on 2006-11-24
Hello all. I am currently using this computer for a Counter-Strike Source server, and it's working great (a lot easier than when I had it on Windows, I might add.) So, this server keeps track of stats. I want to upload these stats regularly to a mysql database. On my website, I can have a stats page that accesses this database. My problem however, is updating the mysql database regularly. If I wrote a php script to write the stats to the database, how could I set it up in Ubuntu to, say, execute every 10 minutes? How would I do this, and is it possible? Thanks for your help.

Edit: I know how to write the script, but I need help setting the script up to regularly execute.

---

### Post by wastrel on 2006-11-24
cron, the periodic job scheduler, is used to automate tasks like this.

```
man cron
```  and  ```
man crontab
``` should get you started

---

### Post by roflcopter_1 on 2006-11-24
Thanks for the reply! I'll look for some info. You're sure that this can be used to execute php scripts, though, right?

---

### Post by scxtt on 2006-11-24
any command that can be run from the CLI can be made a cron job ... something like:

0,10,20,30,40,50 * * * * <user> php5 /path/to/file.php

should work if you add it to /etc/crontab as root ... (and have php5 installed, and it's in the users path) ...

---

### Post by roflcopter_1 on 2006-11-25
Argh, I got the script done, tried running it with CLI and mysql_connect not defined. This is my only problem with linux, figuring out all the little stuff to install. It's no one's fault but my own, but still a hassle. Once I get it figured out I guess I'll do that and post again.

Edit: What would I most likely need to do if I'm getting this error: Warning: mysql_connect(): Can't connect to MySQL server on

I connect fine with the same login on my website. How exactly should I have php.ini configured?

---

### Post by roggnroll on 2007-01-25
I'm having the same problem.
I run **Xampp** on my Linux PC,
but how can I *[I][I]execute a PHP*[/I] Script *regularly*[/I]?
I tried ```
gnome-open
``` to open an url, it works fine, but can't I load a page without showing it?
Or if there's no other possibility, how to close firefox after that?
> 0,10,20,30,40,50 * * * * <user> php5 /path/to/file.php
that is not working, as I'm running Xampp.
Please help!

---

### Post by kalikiana on 2007-01-25
I didn't ever try to run a php app from cli but how about something like this:

curl [http://localhost/my/file](http://localhost/my/file)

This will simulate a real browser downloading the page and trying to render it, thus it's run as though as it were opened in a browser.

---

### Post by Nik_Doof on 2007-01-25
> **roflcopter_1 said:**
> Edit: What would I most likely need to do if I'm getting this error: Warning: mysql_connect(): Can't connect to MySQL server on

I connect fine with the same login on my website. How exactly should I have php.ini configured?

Check your /etc/php4/cli/php.ini (or /etc/php5/cli/php.ini if running php5) for a line like:

```
extension=mysql.so
```

Also, either the error got trimmed or its trying to connect to "", so possibly its a script error.

---

### Post by roggnroll on 2007-01-25
> **kalikiana said:**
> 
curl [http://localhost/my/file](http://localhost/my/file)

command not found

---

### Post by RobNY on 2007-01-25
To run a PHP script from the command line (or through CRON), edit the script to add the following as the first line before the <? in your source file:

#!  /usr/bin/php -q
<?
your source
?>

Use "which php" (no quotes) in a terminal to determine the exact location of your PHP CLI.

Make sure the PHP script is chmod'd as executable.  See man page for chmod.

You can enable the mysql module in the CLI version of the INI by editing: /etc/php5/cli/php.ini   I like that the default install allows for separate INI files for CLI and web.

Lastly, if you are running a PHP script as a cron job, you should think about redirecting the output (stdout/stderr) to somewhere...

Hope this helps.

---

