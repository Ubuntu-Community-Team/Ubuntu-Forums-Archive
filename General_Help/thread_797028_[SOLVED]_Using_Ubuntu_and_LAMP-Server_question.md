---
title: "[SOLVED] Using Ubuntu and LAMP-Server question"
date: 2008-05-16
forum: General Help
---

### Post by chaoswings on 2008-05-16
I installed the LAMP server using

sudo tasksel install lamp-server

and I have installed  phpmyadmin and mysql-admin

1) I am using this as a sandbox and I only want the server to be accessible on my local network, how can I make sure it is not available to the outside?


2) Is there anyway I can make shutting down/restarting the server easier to do (is there a GUI?)?

I'm using the latest ubuntu release.

---

### Post by jimv on 2008-05-16
If you're hooked to the internet via router, you have to specifically forward a port through the router to that box in order for it to be exposed to the outside world.

---

### Post by Timbothecat on 2008-05-17
I'm building a web site at the moment and I'm trying to use a form with it. I was going to use a site called response-O-matic to take care of the form action etc but I can't seem to get it to work to my satisfaction.

"No worries", I thought. I'll just learn PHP and chuck in a script to take care of the form behaviour. Sounds easy enough. Except that php isn't installed on my Ubuntu 8.04 system. So I go to the repository and try to install it from there but there are so many php apps listed that I had no idea where to start.

Next step, LAMP. I found this thread and thought my prayers had been answered until I got this:
```
user@desktop:~$ sudo tasksel install lamp-server
[sudo] password for *user*: 
tasksel: aptitude failed (100)
user@desktop:~$ 

```

Does any one know how I can get php installed on my system so that I can run a simple php script in a web browser? Alternatively, does anyone know how I can fix the error massage above so that I can just install LAMP-server and be done with it?

Any help is greatly appreciated.

All the best,

Tim.

---

### Post by chaoswings on 2008-05-17
For you to use the command I posted you must have ubuntu 8.04 or the previous version I believe.

If you do have 8.04 it could have failed due to a connection problem or you need to update the repositories.

If you are using an earlier version and just want php installed try this...
[B]
sudo apt-get install php5[/B] 

 You also have to configure various things go to :

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

If you still need help PM me or post in the thread.


Thanks Jimv I believe that answered my question.

---

### Post by ThePHPguy on 2008-05-17
I recommend Xampp for Linux it installs Apache, MySQL, and PHP.

[http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

---

### Post by Timbothecat on 2008-05-17
What do you do if you go to edit your httpd.conf file and it's empty?

According to the link from chaoswings my problem is that I don't have server name changed to localhost. So I started up the editor with the above file and it was blank. I know that this is a file I've had to change in the past (years ago) but is it still used?

Anyway, I got the lamp-server to install last night but I still can't view php files or find the local host when I enter that into the address bar. I might un-install the app's in question and start again using the link that chaoswing put in earlier.

I probably won't get to this for a couple of days though so I'll let you know how it all turns out.

All the best,

Tim.

---

### Post by chaoswings on 2008-05-18
I think apache2 does not use httpd.conf file anymore. I believe it uses apache2.conf. You can still create the file and it will read it, but apache2.conf will have higher priority if a conflict arises.

Do you get any errors starting or stopping apache2?

also if you install phpmyadmin you need to add

```
#enable phpmyadmin to work
Include /etc/phpmyadmin/apache.conf  
```to the bottom of **apache2.conf** then you can access it at [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

In** httpd.conf** I have just one line:

```
Servername localhost
```


Also are you accessing the server from the same machine that is running it? If you are accessing it from another PC on your LAN you may need to change the bind address and Listen ports etc. I'm still trying to figure that out as we speak. Any step by step instructions are appreciated (i.e. what file to edit and what lines to insert).

---

### Post by Timbothecat on 2008-05-18
Hi Chaoswings.

I didn't receive any errors restarting apache2. But I still don't see the web page when I enter "http://localhost". It just keeps telling me that "Firefox can't establish a connection to the server at localhost."

I have solved my initial problem by signing up to a site that handles forms by putting their data into my form (rather than the other way around) but I'd really like to learn to handle forms through PHP so that I can have more control over the forms on the web sites that I build.

Anyway, I'll try a few more things and get back to you with the details in the coming days.

All the best,

Tim.

---

### Post by chaoswings on 2008-05-19
Why don't we try something....

I have attached my apache2 folder to this post. Backup your apache2 to a safe place and then paste in mine. It's quick and dirty but lets see if it works.

If it works then leave it. If it fails try only using my apache2.conf.

Note that I'm using ubuntu 8.04 but I don't think that should make a difference. Also do you have any firewalls or ipfilters running that may block it?

If you are really desperate you can remove everything (it's in the link I posted in the past)

Or you could start ubuntu over from scratch and install the server edition and then install the desktop on top of it so you have a GUI. You just run the ** sudo apt-get install ubuntu-desktop** command.

---

### Post by Timbothecat on 2008-05-19
Hi Chaos.

You'll need to bear with me a bit mate, I'm somewhat of a Linux newbie.

I managed to get the file unzipped and put in to the /etc folder after much crowbarring (mainly of my head -frustration at not being able to remember commands etc) and then I restarted the apache2 server and got this: 

```
Warning: DocumentRoot [/home/*your-file*/public_html] does not exist
```

I was originally leaving my document root where it was because I'm never sure of what needs to move when you move it. This is one of the disadvantages of learning specifically (which I did in my course) because it's very hard to port a classroom lesson to something else under those circumstances. You're much better off learning ***WHY*** something works because then you can take that knowledge and apply it to many different situations. This is why I'm here though. To un-learn my bad habits and then learn the right way.

Anyway, my document root won't be the same as yours (I've changed it above, I assume you know what the original was :):popcorn: ). I do need to know what I have to put into such a file and also where I need to go to add the corrected path.

I hope this isn't asking too much, but if you could give me a brief explanation of how this .conf file works I may be able to understand more about what I put into it and why I have to. Only if you have some time to spare.

Thanks mate.

All the best,

Tim.

P.S. I changed the path of the "Default" in /etc/apache2/sites-available/default from your user name to mine and then added the folder in the required directory. I now have an index page coming up but nothing in it (as I haven't placed anything in there as yet. Is the Apache home page (with the feather etc) supposed to come up and if so where do I find that to put it in the public_html folder?

---

### Post by chaoswings on 2008-05-20
Basically the apache2.conf file for lack of a better word the master configuration file. As I mentioned before if a conflict arises between apache2 and other configuration files apache2.conf will either take priority or it will result in an error or warning.

**I should mention that # means that line is considered a comment and is not included in actual code and therefore it is ignored and not executed.** 

You will see lines of code that are commented out for example:

```
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

```In this block the only line that is executed is **LockFile /var/lock/apache2/accept.lock** everything else is ignored.


You will notice that in the apache2.conf file there are many lines resembling the following structure:

 Include <name of config file goes here>

Every single .conf file in the apache2 directory has an Include line.

For example,

```
# Include ports listing
Include /etc/apache2/ports.conf
```If we were to say remove the lines:

```
# Include all the user configurations:
Include /etc/apache2/httpd.conf
```The server would ignore the httpd.conf file. I should mention that anything you write in the other .conf files can be written directly into apache2.conf. The reason you shouldn't is because it keeps your code clean and organized.

Most of the file is well commented out and tells you what each line does. So I won't go into further explination unless you ask me to.

The other files are pretty obvious


**envvars.conf** Stores the environment variables for the server **DON'T TOUCH IT**

**httpd.conf **is what was used in apache1. Apache2 uses apache2.conf it is just there for backwards compatability.

**Ports.conf** tells the server what ports to listen to.

For example if you add

```
Listen 192.168.2.163:80
```The server will only listen to requests coming from that port and that specfic IP address.

now if you look in **sites-availible/default.conf**

That is the default file for all sites that you create on the server. You could make another configuration for a different site if you wanted.

This file** tells the server where your root directory of your website will be as well as other basic things such as where to store cgi-scripts.**

you will notice in mine I changed **/var/www** to** /home/redchaos/public_html**

so now it will look for my site html files in the public_html folder in my home directory. Instead of /var/www directory.

That's pretty much all you need to know. If anyone sees an error in my post don't be afraid to point it out. Did I manage to clear things up a bit?

---

### Post by Timbothecat on 2008-05-20
Top job Chaos.

Thanks heaps mate, I'm actually starting to understand this stuff a little better now.

I was actually under the impression that the Apache home page (actually the local host but an apache html file) was supposed to come up when you put in the address for localhost. Does that still happen with apache2? Or is that just an apache1 thing? I know it wouldn't in my situation because I don't have the file in my web root but I would love to know if this is still the case.

Anyway, thanks again mate.

All the best,

Tim.

---

### Post by chaoswings on 2008-05-21
Your welcome.

One last thing, if your web root folder does not have an index file (i.e. index.php, index.html etc.) It normally shows a crude file tree with links to all the files in the folder. That is normal.

---

