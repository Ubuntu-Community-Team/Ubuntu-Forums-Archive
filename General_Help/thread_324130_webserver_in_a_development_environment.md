---
title: "webserver in a development environment"
date: 2006-12-23
forum: General Help
---

### Post by camilluk on 2006-12-23
Hello!

I would like to start learning PHP. I never did any web development before, and what I want to do is to create a browser based application to retrieve and display information from a database and it should be server based so I don't need to install it on all my LAN's pc's, and so the processing is made by the server. Currently however, I'm just working on my own machine running Kubuntu Edgy.

From the tutorial and threads I read so far I gathered that I needed to install a webserver and PHP. So I did, using Synaptic, and installed Apache2 and PHP5, as well as MySQL since ultimately I want to work with a database.

Maybe all this is a bit premature for me, but all the documentation I read makes a lot of assumptions on what the reader (in this case me) knows.

So here it goes:
What am I supposed to do after the installation of apache and php?? I don't see any items on the menus... and I'm not sure if and what I need to configure to make 'something' happen! I read somewhere that the httpd.conf and some similar files need to be configured, but they're not in the same path as the tutorials suggest and their content is either totally different from what I expect or even empty.

I also read that to test the configuration you need to create a .php document, the content of which is the only understandable thing to me in this whole story!, and put it in the webserver default folder. Then try to open the file via a browser. I tried a few locations and they must not be right as the page doesn't load. I'm also supposed to use an address such as http:\\localhost\something, or http:\\192.168.0.100\something, but of course:
1. I have no idea of where the default folder for the webserver is
2. what is the IP address of the webserver?

I have loads of other questions about the subject, but I guess I should find an answer to these first, and hopefully things will get clearer...

Thanks for any help!
Cam

---

### Post by koenn on 2006-12-23
> but all the documentation I read makes a lot of assumptions on what the reader (in this case me) knows
That's quite common in documentation, including manuals and tutorials. The authors usually assume you more or less understand what you're trying to achieve, and limit themselves to the info pertaining to the subject, not all the background knowledge you need -- that, you should get elsewhere.  Can't really blame them :-)

Here's a quick start crash course
1- your setup is called a "LAMP" : Linux, Apache, MySQL, PHP, basically Linux + a webserver (or http daemon), a database, and php, a scripting language to glue everything together, eg retrieve data from the database and turn them into html that the webserver can serve to the clients

must-read documentation if you're new tothis :: the Ubuntu Server Guide 
[http://doc.ubuntu.com/ubuntu/serverguide/C/networking.html](http://doc.ubuntu.com/ubuntu/serverguide/C/networking.html)

2- You shouldn't expect anything to work by clicking icons or menu-items: servers typically run without graphical user interface (GUI) so you install and configure from a command line. If you're experimenting with server apps on a desktop computer (eg with Edgy), you'll work in a terminal. 

3- > installed Apache2 and PHP5, as well as MySQL since ultimately I want to work with a database.
for a LAMP server, you usually need to install some additional modules for php to work with  mysql, apache to wotk with php, and so on. Check the server guide. Maybe synaptic took care of it with dependencies and recommends, maybe not.

4- You may need to edit some configuration files for things to work - re. The Server Guide. Other than that, servers usually start their services (daemons) automatically so you don't need to look for menu-items to start them. There just there, up and running, and waiting until you ask them to do something (like get a web page, execute a php statement, or retrieve data from a database)

5-> I'm also supposed to use an address such as http:\\localhost\something
don't use back-slashes (\), those are only valid in Windows paths

6-> 1. I have no idea of where the default folder for the webserver is
it varies and is configurable, but ubuntu uses /var/www I think. It's set ad "DocumentRoot" in the apapche config. 
[http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html#http-configuration](http://doc.ubuntu.com/ubuntu/serverguide/C/httpd.html#http-configuration)

7- > 2. what is the IP address of the webserver?
it's the IP address of the computer where the webserver is running. 
For you that may be 127.0.0.1 (or 'localhost') because probably you're running the http daemon (apache) and the http client (Firefox ?) on the same machine. In real live, you'd need the ip address (or hostname or fully qualified domain name) of the computer - and preferably a fixed address, no dhcp.

---

### Post by camilluk on 2006-12-24
Thank you koenn!

> **koenn said:**
> The authors (...) you should get elsewhere.  Can't really blame them :-)
I totally understand. Mine wasn't a complaint... I just didn't know what  to look for, hence this thread.

> **koenn said:**
> must-read documentation if you're new tothis :: the Ubuntu Server Guide I will do this asap. Hopefully it will shed some light.:cool:

> **koenn said:**
> don't use back-slashes (\), those are only valid in Windows pathsBad habits are hard to break!!!

Thank you for taking the time to help! I appreciate it!
Have a Merry Christmas!

---

