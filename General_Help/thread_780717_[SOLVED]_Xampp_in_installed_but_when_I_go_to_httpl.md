---
title: "[SOLVED] Xampp in installed but when I go to http://localhost there is nothing"
date: 2008-05-03
forum: General Help
---

### Post by Rytron on 2008-05-03
Hi,
I have installed Xampp. I use Xampp Control Panel to start all Xampp services. 

When I go to my browser and type:

```
http://localhost 
```

- there is nothing on the screen.

Also regarding the folder: /opt/lampp
I went to properties and noticed that
1. nobody owns it
2. root is the group

Any help much appreciated. Bye.

---

### Post by Rytron on 2008-05-25
I go to the terminal and type
```

:~$ sudo /opt/lampp/lampp start
```

Here is the output I get:

```
Starting XAMPP for Linux 1.6.6...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.
```

I do not know what other web server is in use. I have apache2 installed and I want to use this. Please help.
Cheers.

---

### Post by Monicker on 2008-05-25
I believe xampp uses it own version of apache, so most likely you will need to uninstall the ubuntu package first.

To verify what else is listing on port 80:
```

sudo netstat -anltp|grep :80
```

---

### Post by Sarah L on 2008-05-25
On my XAMPP install, the lampp folder is owned by root, but I don't think this has much to do with your problem. If you think it might affect it, try using chown to set the ownership back to root.

Reboot your computer and try starting lampp from the command line to make sure there aren't any stale processes running in the background.

You mentioned that you have Apache2 installed. Is that part of a separate package or installation? Another installation might be set to run at startup and thus compete with lampp. Remove all other web servers that you've installed on your system and try lampp again.

Hope this helps,
Sarah

---

### Post by Rytron on 2008-05-25
> **Monicker said:**
> I believe xampp uses it own version of apache, so most likely you will need to uninstall the ubuntu package first.

To verify what else is listing on port 80:
```

sudo netstat -anltp|grep :80
```

Hi,
I tried ```
sudo netstat -anltp|grep :80
```

Here is the output:

```
:~$ sudo netstat -anltp|grep :80
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      6296/apache2 
```

So I presume I need to uninstall apache2? What web server is used by Xampp?

---

### Post by Rytron on 2008-05-25
> **Sarah L said:**
> On my XAMPP install, the lampp folder is owned by root, but I don't think this has much to do with your problem. If you think it might affect it, try using chown to set the ownership back to root.

Reboot your computer and try starting lampp from the command line to make sure there aren't any stale processes running in the background.

You mentioned that you have Apache2 installed. Is that part of a separate package or installation? Another installation might be set to run at startup and thus compete with lampp. Remove all other web servers that you've installed on your system and try lampp again.

Hope this helps,
Sarah

Hi Sarah L, I'm not sure if apache2 was installed with Xampp or whether it was installed before Xampp was installed. I think Apache comes preinstalled with Ubuntu but I may be wrong about that.

---

### Post by CodeCruncher on 2008-05-26
Ok first of all we need to know witch ubuntu you installed was it the Desktop or the server?


I recently installed the Desktop version and then installed Xampp and everything was fine.

To see if xampp is running try this as root 

```
/opt/lampp/lampp security
```


Then if you get a response then you know xammp is running! in your web browser try putting in the ip address of that computer instead of localhost.


then try localhost/webalizer    you should get a stats page


good louck

---

### Post by Monicker on 2008-05-26
> **Rytron said:**
> 
So I presume I need to uninstall apache2? What web server is used by Xampp?

xampp comes bundled with its own version of apache.  You need to uninstall the Ubuntu specific apache package, so that the one included with xampp can run.

---

### Post by Rytron on 2008-05-27
> **CodeCruncher said:**
> Ok first of all we need to know witch ubuntu you installed was it the Desktop or the server?


I recently installed the Desktop version and then installed Xampp and everything was fine.

To see if xampp is running try this as root 

```
/opt/lampp/lampp security
```


Then if you get a response then you know xammp is running! in your web browser try putting in the ip address of that computer instead of localhost.

then try localhost/webalizer    you should get a stats page

good louck


Hi,
The desktop version is installed.

---

### Post by Rytron on 2008-06-01
Hi,
I got rid of Xampp.
Installed Lamp in Symantic. Then I came across this page: [http://www.darcynorman.net/2007/01/01/ubuntu-server-not-seeing-localhost/](http://www.darcynorman.net/2007/01/01/ubuntu-server-not-seeing-localhost/)
and uncommented the appropriate lines in interfaces file.

Eureka. I can view the index.html file in /var/www
I still cant view php files yet.

Correction. It does work.

---

