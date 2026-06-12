---
title: "ktorrent web interface cant find PHP"
date: 2007-08-15
forum: General Help
---

### Post by go_dragons on 2007-08-15
First of all I would like to say thank you in advance for any help I recive here. I have been using linux now for about a year and I am highly impressed with the support and information provided in these forums and other ubuntu-related locations. no other distrobution I have tried so far has provided support quite as readily as ubuntu.


I use a torrent client frequently to download files onto my server. I will be going away for a few months and I need a way to administer my server without being physically next to it. One of the ways I decided to do that is by installing ktorrent because it has a handy web interface that I could access remotely.

I installed ktorrent through apt and then loaded the web interface plugin. When I tried to configure the interface it gives me this error:

"Php executable isn't in default path, please enter the path manually"

I then installed php5 as well as apache2 through apt but the error message is still there. 

I used the locate command to try to find the php executable but I could not find it. Does anybody know where this executable can be found? OR is there another program that has a working web interface?

 I have included pictures of the error message in ktorrent as well as what happens when I try to logon to the web interface in case that helps anybody.   Thanks for your help.

---

### Post by Darkhack on 2007-08-15
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/php5/+bug/47858](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/47858) [br].[/br] ---------------------------- [br].[/br] 
It appears as though the version of PHP in Ubuntu's repository doesn't install it to the typical location that other applications search for.  There is a bug report with a similar problem that someone was having with php-pear.  Try creating a symbolic link as shown in the bug report and see if it fixes your problem...

> 
The /usr/bin/pear script wrongly looks in /usr/local/bin/php and /usr/local/lib/php for the php binary and pear scripts respectively. These are not the directories where ubuntu installs these files. My quick (and nasty) fix was to put symbolic links as follows to redirect the program to the correct directories:

sudo ln -s /usr/bin/php /usr/local/bin/php

sudo ln -s /usr/share/php /usr/local/lib/php


---

### Post by shaydee on 2007-08-16
> **go_dragons said:**
> 
OR is there another program that has a working web interface?


Yes, at the moment two useful alternatives come into my mind.

1.) For Azureus there is a Java based web interface plugin ([link]("http://azureus.sourceforge.net/plugin_details.php?plugin=webui")). By "Java based" I mean that the client side of the interface needs a web browser that is able to execute Java applets. Azureus itself on the server side needs Java as well, of course. 
If you have physical access to your server at the moment, and if it has a monitor, then setting up the plugin should be much easier than any solution that requires a 3rd party webserver (such as apache). 

2.) rtorrent is a nicely slim and efficient console based torrent client. You could install it (even remotely) on your server and then access it via ssh. One warning, though: The Feisty packages of rtorrent/libtorrent are outdated and shouldnt be used. This means you'd have to compile those two (rtorrent depends on libtorrent) by yourself (but thats not that hard). 
[http://libtorrent.rakshasa.no/]("http://libtorrent.rakshasa.no/")


> 
"Php executable isn't in default path, please enter the path manually"

> 
sudo ln -s /usr/bin/php /usr/local/bin/php


That does sound like a good idea. 
One way to find a file or symlink goes like this:
```

find /usr -type f -name php
find /usr -type l -name php

```

---

### Post by lqyjzmms on 2007-08-18
I fixed this by installing the packages php5-cli and php-pear. Afterwards, I set the PHP executable path to /usr/bin/php. The light in the settings window turned from red to green and the Web GUI of KTorrent worked.

---

### Post by KaroSHiv0n on 2007-08-29
I have installed the packages above and the light is green but i can never get past the login screen :/

---

### Post by lqyjzmms on 2007-08-30
Did you set your login data in the plugin's properties dialogue?
Do you access the web interface using a host name like [http://localhost:8080/](http://localhost:8080/) or using an IP address ([http://127.0.0.1:8080/](http://127.0.0.1:8080/))?

---

### Post by KaroSHiv0n on 2007-08-31
> **lqyjzmms said:**
> Did you set your login data in the plugin's properties dialogue?
Do you access the web interface using a host name like [http://localhost:8080/](http://localhost:8080/) or using an IP address ([http://127.0.0.1:8080/](http://127.0.0.1:8080/))?

yeah i set a username/pass and i access it via ip:8080 i can get to the login area fine but when i click login/hit enter it seems to refresh but nothing actually happens.

---

### Post by lqyjzmms on 2007-09-01
Please try to use a host name to access the web interface instead of the IP address.

---

### Post by KaroSHiv0n on 2007-09-01
> **lqyjzmms said:**
> Please try to use a host name to access the web interface instead of the IP address.
doesent connect at all just trys to connet to a .com address.

---

### Post by lqyjzmms on 2007-09-02
You can solve this by adding an entry to your /etc/hosts file.

For example, to access a computer with the IP address 1.2.3.4 using the hostname ktorrent add the following line to /etc/hosts:

```
1.2.3.4       ktorrent
```

---

### Post by KaroSHiv0n on 2007-09-02
> **lqyjzmms said:**
> You can solve this by adding an entry to your /etc/hosts file.

For example, to access a computer with the IP address 1.2.3.4 using the hostname ktorrent add the following line to /etc/hosts:

```
1.2.3.4       ktorrent
```

Ok i edited the hosts file and can now connect via hostname but still nothing happens, it refreshes and wipes the details but never connects, ive tried turing off firestarter also but that made no change.

---

### Post by stoeptegel on 2007-09-02
Isn't is php5-cli we need to install here?

---

### Post by KaroSHiv0n on 2007-09-10
> **stoeptegel said:**
> Isn't is php5-cli we need to install here?

[2235][beef@Goldstein:~]+ sudo apt-get install php5-cli
Reading package lists... Done
Building dependency tree       
Reading state information... Done
php5-cli is already the newest version.


not that =(

---

### Post by VeVhLoS on 2008-02-21
post #4 solved the case for me
thanks

---

