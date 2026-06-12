---
title: "Cant run cron job as www-data"
date: 2016-08-18
forum: General Help
---

### Post by astarmathsandphysics on 2016-08-18
I have several websites in /var/www/ each in a folder. The folders are owned by www-data.
I have installed google sitemap generator and have set up cron jobs for each domain to run the sitemap script as www-data.
The cron job will not run, and neither when I run it under root as www-data/
How can I run cron jobs as www-data?
Using ubuntu 14.04

---

### Post by Keith_Helms on 2016-08-19
Probably just setting up a crontab for that user would work
```
sudo crontab -e -u www-data
```

---

### Post by astarmathsandphysics on 2016-08-19
No cron job works on that crontab

---

### Post by SeijiSensei on 2016-08-19
The www-data user is not able to invoke a shell by default.  In /etc/passwd you'll see
```
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
```
If you want to be able to run scripts as that user, you'll need to change "/usr/sbin/nologin" to "/bin/bash".

---

### Post by astarmathsandphysics on 2016-08-19
Is it safe to do that? Will www-data be able use terminal without a passwoed?

---

### Post by Habitual on 2016-08-19
> **astarmathsandphysics said:**
> Is it safe to do that?
Great Question!
By default, I don't believe **www-data has ever had a password.**
It's not a user, it's a service. We trust services differently than we trust users. :)

Open a terminal and try this either with or without sudo
```
su - www-data
[sudo] password for <you>: 
```
and it should say
```
No directory, logging in with HOME=/
This account is currently not available.
``` if the shell is nologin. 
If the shell is bash for www-data and you ran that, it will execute.

Running a script as www-data that needs a shell and a bash login shell where www-data has never had a password set.

Sounds ok to me. Like I said Great Question!"
Wait for additional input.  It is just my opinion.

---

### Post by astarmathsandphysics on 2016-08-19
Thanks. Will follow your advice

---

### Post by Habitual on 2016-08-19
You're welcome.
I'm just one person and there's a few around here who can either agree or disagree with my assessment.
Or offer a completely new take on another solution. 

Love Linux for flexibility.
Peace.

---

### Post by SeijiSensei on 2016-08-20
> **astarmathsandphysics said:**
> Is it safe to do that? Will www-data be able use terminal without a passwoed?

If you give www-data a shell, but do not give the account a password, then you can only use the account after first becoming root and then using "su www-data".  Without a password you cannot log in directly.

I sometimes enable a shell for the Apache user especially to test permissions.  For instance, if I become the www-data user, then I can test where the user can write files with "touch /path/to/some/dir/test".  While I don't let the Apache user write into the web tree, e.g., /var/www/html, I do let it write into specific directories outside the DocumentRoot so that PHP scripts can put files in those locations when needed.

---

### Post by astarmathsandphysics on 2016-08-20
I have put this line in root crontab

0 12 20 * *  sudo -u www-data /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

and tested it in root consoles as 

sudo -u www-data /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

This returns the message

The Sitemap type is WEB Sitemap.
[ERROR] Can not locate file: /var/log/apache2/astarmathsandphysics.log
Configuration file errors -- exiting.

---

### Post by astarmathsandphysics on 2016-08-20
The file /var/log/apache2/astarmathsandphysics.log soes exist and all directories in this path are readble

---

### Post by SeijiSensei on 2016-08-20
Try adding it to /etc/crontab instead like this:
```
0 12 20 * * www-data /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml
```
Any better?

---

### Post by astarmathsandphysics on 2016-08-21
That doesnt work unfirtunately

---

### Post by SeijiSensei on 2016-08-21
Why not just run the Google generator app as root?  I don't really see why you need it to run as the www-data user.

---

### Post by astarmathsandphysics on 2016-08-21
I could but I thought it would be bad practiice to have a file owned by root accessible via the internet. I have gone hot on security this year. All my websites have gone hhtps, I have a static ip now and am using a caching proxy server with ggod security.

How would I edit the cron job to run as root and save as www-data?

---

### Post by Keith_Helms on 2016-08-21
> **astarmathsandphysics said:**
> I have put this line in root crontab

0 12 20 * *  sudo -u www-data /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

and tested it in root consoles as 

sudo -u www-data /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

This returns the message

The Sitemap type is WEB Sitemap.
[ERROR] Can not locate file: /var/log/apache2/astarmathsandphysics.log
Configuration file errors -- exiting.

> The file /var/log/apache2/astarmathsandphysics.log soes exist and all directories in this path are readble

You say the log file does exist.  Is www-data allowed to update that file?  You may be close to having this working and just running into permissions problems.

What does the following give you?

```
sudo -u www-data touch /var/log/apache2/astarmathsandphysics.log
```

---

### Post by astarmathsandphysics on 2016-08-21
as user astarmathsandphysics I get the message

touch: cannot touch &#8216;/var/log/apache2/astarmathsandphysics.log&#8217;: Permission denied

---

### Post by astarmathsandphysics on 2016-08-21
All foldersdown to the file are accessible and file is reable

---

### Post by Keith_Helms on 2016-08-21
> **astarmathsandphysics said:**
> All foldersdown to the file are accessible and file is reable

Yes, but that script you want to run is probably trying to write to the logfile, not just read it.  You need a directory and logfile that the www-data user is authorized to write to.

---

### Post by astarmathsandphysics on 2016-08-21
Ok I will look at that

---

### Post by astarmathsandphysics on 2016-08-21
I opened astarmathsandphysics.log an emptied the contents then saved it without starting rsyslog.
Then I ran 
sudo /usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

and log file was empty when the command finished executing. Probably the script does not write to the file.

---

### Post by SeijiSensei on 2016-08-22
> **astarmathsandphysics said:**
> I could but I thought it would be bad practiice to have a file owned by root accessible via the internet.

Not really.  All Google does is download the file.  Also the file won't be executable.

If you're really paranoid about this, run the script as root and include
```

chown www-data:www-data /path/to/the/file
chmod 444 /path/to/the/file

```
at the end of the script.

---

### Post by astarmathsandphysics on 2016-08-22
I will execute as root and have written another cron job to change owbership of all files in /var/www to www-data:www-data once a week.
Once is not enough because the script generates more files periodically and these are owned by root.

---

### Post by Keith_Helms on 2016-08-22
> **astarmathsandphysics said:**
> I will execute as root and have written another cron job to change owbership of all files in /var/www to www-data:www-data once a week.
Once is not enough because the script generates more files periodically and these are owned by root.

So you have the script running successfully as a cron job now?

---

### Post by SeijiSensei on 2016-08-22
> **astarmathsandphysics said:**
> I will execute as root and have written another cron job to change owbership of all files in /var/www to www-data:www-data once a week.
Once is not enough because the script generates more files periodically and these are owned by root.

I was speaking more about writing a "wrapper" script that invokes the Google map generator and then changes the ownership.  Something like this:
```

#!/bin/bash
MAP=/path/to/the/map.xml

chown root:root $MAP
chmod 600 $MAP

/usr/bin/google-sitemapgen --config=/usr/share/doc/google-sitemapgen/examples/astarmathsandphysics.xml

chown www-data:www-data $MAP
chmod 444 $MAP

```

---

### Post by astarmathsandphysics on 2016-08-24
I will try that

---

