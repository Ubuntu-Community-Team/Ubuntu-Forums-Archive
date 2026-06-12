---
title: "Getting Apache to recognize PHP"
date: 2005-05-01
forum: General Help
---

### Post by fractalvibes on 2005-05-01
Php is installed in this Ubuntu system, Apache seems to know it is there.  The PHP config file looks like when viewed through the Webmin "Edit Config Files" page:
```

<IfModule mod_php4.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

The virtual  server page for the default server has a PHP link to a page,
On the PHP for default serverpage, the PHP configuration values and PHP configuration flags are blank.  I suspect that may be the problem, as PHP is served up as text (not being parsed and executed by the PHP engine)

Any clue as to what goes there?

thanks,

fv

---

### Post by bnutting on 2005-05-02
I believe that if you have apache2 installed you may need to go to your /etc/apache2 directory and edit the apache.conf file. In it you should see a few line referring to php, you will need to uncomment those lines. 

Sorry for any errors with file names and locations but I am not on my Ubuntu laptop right now. The above information should at least point you in the right direction.

You could also look at the [http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by fractalvibes on 2005-05-02
Thanks,

The apache2.conf file has nothing commented or not that mentions php, so I am guessing that I need to add a line or two pointing to the php conf files?

fv

---

### Post by hobbestec on 2005-05-02
You probably need to add the Load Module command in there wherever you have other LoadModule commands.

eg:

LoadModule php4_module libexec/libphp4.so

---

### Post by bnutting on 2005-05-02
You realy should not have to 'add' anything. Have you checked out the ubuntuguide.org site yet? There is a simple step-by-step to get mysql/apache2/php to all work together. 

I have it all working and all I had to do was uncomment the couple of lines that mention php.

Just trying to get the "simple" solution :|

---

### Post by fractalvibes on 2005-05-02
I looked at the apache2.conf file and there are no lines that mention php...???

---

### Post by bnutting on 2005-05-02
When you installed apache2 what package did you install?
```
sudo dpkg -l | grep apache
```

The ubuntuguide.org site mentions apache2 package. There is also an apache package which is 1.3.33. I wonder if you installed the apache package rather than the apache2 package?

---

### Post by fractalvibes on 2005-05-02
I'll check after work - pretty sure it was apache2, but anything is possible....

So sudo dpkg -l | grep apache 
will show me all packages that have apache in the name?

fv

---

### Post by fractalvibes on 2005-05-02
Yep - apache2 alright.
the command:
So sudo dpkg -l | grep apache 

reveals:

apache2 2.0.53-5
apache2-common 2.0.53-5
apache2-mpm-pr 2.0.53.5
apache2-utils2.055.5
libapache2-mod 4.3.9-1
libapache2-mod 4.3.10-10
webmin-apache 1.160-2


fv

---

### Post by dewey on 2005-05-02
Apache2 is horrible with php.  If you can help it, use Apache 1.3.* for PHP.
[http://apache.slashdot.org/article.pl?sid=04/12/21/1837209](http://apache.slashdot.org/article.pl?sid=04/12/21/1837209)

---

### Post by bnutting on 2005-05-03
Ok, lets see if we can get this thing working.
You had stated:
> Php is installed in this Ubuntu system, Apache seems to know it is there. What do you mean by that?
I have 5 files that have the word php in it (these are all listed in my /etc/apache2/ directory):
```
apache2.conf
mods-available/php4.conf
mods-available/php4.load
mods-enabled/php4.conf
mods-enabled/php4.load
```

In my apache2.conf file, I have the following lines in it:
```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
#AddType application/x-httpd-php .php
#AddType application/x-httpd-php-source .phps
```

In my mods-enabled/php4.load file, it contains:
```
LoadModule php4_module /usr/lib/apache2/modules/libphp4.so
```

In my mods-enabled/php4.conf file, it contains:
```
<IfModule mod_php4.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>
```

The two above files are just symbolic links to the mods-available ones.
I wonder if it may be the webmin tool that may have messed things up, I have seen in the past where it did when trying to configure a ftp server.

Anyway I hope the above files may be of some use. Let me know hwo you make out.

Bryan

---

### Post by bnutting on 2005-05-03
And another thing, here is a listing of packages that are installed on my system:
```
dpkg -l | grep php
ii  php4           4.3.10-10ubunt server-side, HTML-embedded scripting languag
ii  php4-cgi       4.3.10-10ubunt server-side, HTML-embedded scripting languag
ii  php4-cli       4.3.10-10ubunt command-line interpreter for the php4 script
ii  php4-common    4.3.10-10ubunt Common files for packages built from the php
ii  php4-mysql     4.3.10-10ubunt MySQL module for php4
ii  php4-pear      4.3.10-10ubunt PEAR - PHP Extension and Application Reposit
ii  php4-universe- 4.3.10-10ubunt Common files for packages built from the php
ii  phpmyadmin     2.6.1-rc1-1    A set of PHP-scripts to administrate MySQL o

dpkg -l | grep apache
ii  apache2        2.0.53-5ubuntu next generation, scalable, extendable web se
ii  apache2-common 2.0.53-5ubuntu next generation, scalable, extendable web se
ii  apache2-mpm-pr 2.0.53-5ubuntu traditional model for Apache2
ii  apache2-utils  2.0.53-5ubuntu utility programs for webservers
ii  libapache2-mod 4.3.9-1ubuntu1 Apache 2 module for MySQL authentication
ii  libapache2-mod 4.3.10-10ubunt server-side, HTML-embedded scripting languag

```

---

### Post by fractalvibes on 2005-05-03
This is on a home machine, so I'll have to check after work.  The apache2.conf did indeed have the two php-related lines commented out, so I uncommented.

In the Webmin app, when I go to the default server and click the PHP icon/link, the php page shows nothing in the conffiguration values or configuration flags.

Let me compare the values posted in the previous two posts with what's on mine
later on today.

Thanks for the assistance!  

fv

---

### Post by bnutting on 2005-05-03
I have not used webmin for this type of admin for quite a while so I don't know how reliable it is for apache2. I would 'abandon' the webmin and rely on the trusty command line with diff/grep/vi along with the logs. You have to remember that a tool like webmin will only show you what it is written to show you, we may be dealing with one of those anomalies.

What happens when you put a .php page in your /var/www directory and open it up with your web browser at: [http://localhost/yourphp.php](http://localhost/yourphp.php) ?

I would try to get apache/php working in the default location prior to moving to your home directory. Allways remember K.I.S.S (Keep It Simple Stupid)  :wink:

---

### Post by fractalvibes on 2005-05-03
I put a test php page in the root directory:

[http://localhost/testphp.php](http://localhost/testphp.php) that just has one line of code to call the phpinfo() function.  When you browse to it it just displays the page as if it was all text.

The webmin tool just puts the contents of the various config files into a textarea like what I am typing this message in.    

Perhaps php4 did not install correctly?  Or a webmin problem?  Will have to check against the previous few posts - could be something very simple!

thanks,

fv

---

### Post by bnutting on 2005-05-03
You could follow the instructions on the ubuntuguide.org site for apache/php4 and instead of just doing a 'apt-get install' do an 'apt-get --reinstall install' this will force apt to redo the install.

Did you have the above files? Did they contain the lines as listed?

I have setup several machines with apache2/php4/mysql and have not had this much trouble.

---

### Post by bnutting on 2005-05-03
This may really seem like a stupid question but your php page looks like this:
```

<?php
phpinfo();
?>
```

I know this seems dumb but I'm running out of ideas.

Bryan

---

### Post by fractalvibes on 2005-05-03
Actually I went home and opened up that php file in gnotepad+ and saw the problem.  The file was created on one of the open office word processors, and it did something like a urlencode on the php tags....

So I stripped all the garbage out and got my phpinfo page just fine!  So it's gnotepad+ only for me from now on (in Linux).

Thanks for all the config info - I should still compare all those files with what was posted...

fv

---

### Post by bnutting on 2005-05-04
Glad things got worked out  :grin: 

I thought things were a bit odd, I was running out of ideas  ](*,)

---

### Post by fractalvibes on 2005-05-04
I should have checked that php file first thing....stupid stupid stupid...

Next challenge - getting MIDI to work....(or not!)

fv

---

### Post by bnutting on 2005-05-04
I guess my question would be, how did the file get messed up in the first place? 
Like I had said before I had an issue with trying to setup an ftp server using Webmin. When I went into the ftp server conf file it was messed up also.

---

### Post by bnutting on 2005-05-04
[QUOTE=fractalvibes]Next challenge - getting MIDI to work....(or not!)[/QUOTE]

Sorry I can not help much with MIDI, but what problems are you having?

---

### Post by fractalvibes on 2005-05-04
I had originally created the file using one of the open office tools
(equivalent to ms word I'd guess).  It took my openng and closing php tags
and urlencoded them to &lt; and &ques;  &gt; and really trashed it out.

MIDI - apparently it takes quite a bit to get this working and routed to the sound card....I have many pages to read...

fv

---

