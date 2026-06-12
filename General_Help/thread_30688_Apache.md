---
title: "Apache"
date: 2005-04-29
forum: General Help
---

### Post by fractalvibes on 2005-04-29
Ok, old machine set up with Ubuntu and Icewm.  I think Apache is also running?
If so, what would be the web root?  (i.e. the equivalent to localhost in IIS).

All my web dev on Apache has been on hosted sites where I could just see my "slice" of the server.

thanks,


fv

---

### Post by shakin on 2005-04-29
[QUOTE=fractalvibes]Ok, old machine set up with Ubuntu and Icewm.  I think Apache is also running?
If so, what would be the web root?  (i.e. the equivalent to localhost in IIS).

All my web dev on Apache has been on hosted sites where I could just see my "slice" of the server.

thanks,


fv[/QUOTE]
 /var/www/

---

### Post by Ronbo on 2005-04-29
If I'm not mistaken it's the location /var/www where the files for the websites are located.  I've played around with Apache2 a bit, but never too seriously.

---

### Post by fractalvibes on 2005-04-29
Ok - thanks!  Can you browse to it as on IIS you would go to [http://localhost?](http://localhost?)

What I see is file:///var/www like file/open would work on windows.

thanks,

Phil

---

### Post by az on 2005-04-29
[QUOTE=fractalvibes]Ok - thanks!  Can you browse to it as on IIS you would go to [http://localhost?](http://localhost?)

What I see is file:///var/www like file/open would work on windows.

thanks,

Phil[/QUOTE]

Did you install apache (actually, ubuntu uses apache2, but you have to install it...)?

either use synaptic or do
sudo apt-get install apache2

---

### Post by fractalvibes on 2005-04-29
Yes, I believe Apache-2 is installed.  WHen I key in
/var/www/  in the address bar, it resolves to file:///var/www/ when it renders.
There I see a subdirectory called apache2-default.

Within that are a number of different index pages in the form of
index.html.NN  where NN is a language code, for example
file:///var/www/apache2-default/index.html.en

Looks like I am just browsing the file system rather than the server serving it up,as one might do in windows for a static html page.  Not sure what needs to be done,  when the system starts up I see apache2 starting from the messages that scroll past.  Don't know if there is an equivalent to the IIS management console
or not....please forgive - new environment for me!

thanks,

fv

---

### Post by shakin on 2005-04-29
Well, rather than posting to ask whether or not you can use [http://localhost](http://localhost), you could have just tried it and seen that it works. Would have been quicker :)

As for configuration, cd into /etc/apache2. Unfortunately I don't have it installed on my home machine so I can't tell you for sure what files are there, but there are several conf files you can edit to do various configuration changes. You can also install webmin or one of several GUI configurators, though somebody else would have to tell you which ones are good because I don't have experience with them.

---

### Post by fractalvibes on 2005-04-29
Point well-taken.   [http://localhost](http://localhost) did work....somehow I thought that was an IIS-only thing for some reason.  Apache is up and running.  Will look into options for a management console of some sort - am just used to using a CPanel on this side of things....used to the M$ MMC admin tools otherwise.

PHP is installed I think - main index page says:
Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4 Server at localhost Port 80

So probably some config files to deal with, as my test php info . php page
just shows me the one line of script and <? ?> tags, so Apache must recognize that PHP is installed, just not running or not configured to  hand off those pages to the PHP engine....

Please bear with me as I ask questions that should be blindingly obvious.....

thanks,

fv

---

