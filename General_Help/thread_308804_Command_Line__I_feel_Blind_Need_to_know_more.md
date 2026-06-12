---
title: "Command Line  I feel Blind Need to know more"
date: 2006-11-28
forum: General Help
---

### Post by Bill007 on 2006-11-28
Kia Ora From NEW ZEALAND

Have installed  server version of ubuntu 6.10

so have no grahical interface

Wanting to set up a production server as well as feed the internet to an internal network from the server there are two network cards in the server box eth0 (recieves the net good) eth1(internal lan) still have issues here but will sort that eventually

Being New to the command line and struggling with the  general directory layout and of course general cammands

Would like to continue with the command line (I like the idea of the challange and have read you get deeper control) but need some clues like how to find things  like

Apache2 and how to see if its running etc 

MYSQL and how to see if its running etc 


PHP5 and how to see if its running etc

etc etc 



I have installed web min and can see it on a remote machines browser hhtp://192.168.1.4:10000 all good

But cant seem to install or upgrade packages etc something not right here cant seem to find certain files


The main thing right now is i want to be able do more from the command line

Regards Bill007

[Taranaki Accommodation]("http://newplymouthmotel.co.nz")

---

### Post by scrooge_74 on 2006-11-28
> **Bill007 said:**
> Kia Ora From NEW ZEALAND

Have installed  server version of ubuntu 6.10

so have no grahical interface

Wanting to set up a production server as well as feed the internet to an internal network from the server there are two network cards in the server box eth0 (recieves the net good) eth1(internal lan) still have issues here but will sort that eventually

Being New to the command line and struggling with the  general directory layout and of course general cammands

Would like to continue with the command line (I like the idea of the challange and have read you get deeper control) but need some clues like how to find things  like

Apache2 and how to see if its running etc 

MYSQL and how to see if its running etc 


PHP5 and how to see if its running etc

etc etc 



I have installed web min and can see it on a remote machines browser hhtp://192.168.1.4:10000 all good

But cant seem to install or upgrade packages etc something not right here cant seem to find certain files


The main thing right now is i want to be able do more from the command line

Regards Bill007

[Taranaki Accommodation]("http://newplymouthmotel.co.nz")



This could be of some help to you [http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)


you can use aptitude to download programas, also you can update your system by doing sudo apt-get update and then sudo apt-get upgrade

---

### Post by atoponce on 2006-11-28
To see what is running, and what isn't, use the 'ps' command.  Something like 'ps aux' will show every process to the screen.

PHP isn't a daemon, so you won't see that in the list.  PHP is a language much like C++, Perl, Python, etc.  None of which have processes.

To start and stop the processes, just use the 'sudo /etc/init.d/' startup and shutdown scripts.  For example, to stop Apache2:

sudo /etc/init.d/apache2 stop

HTH

---

### Post by hearnden on 2006-11-28
Have a look here to get started:  [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

After that, googling for "linux command line" brings up a few more advanced things.

The most primitive way to see if something is running is to look for its program name in the output of 'ps':

```

$ ps -A | grep mysql
$ ps -A | grep apache

```

php does not really 'run' unless someone requests a php page from your web server, so 'ps -A | grep php' will come up blank.

For apache, you can also use:

```

$ apache2ctl status

```

(or 'apachectl' I think if you're not running apache 2).

I don't know if you can test if MySQL is running properly without a MySQL account set up (sounds pretty ridiculous to me), but all the command-line tools appear to want such information, even for just checking if MySQL is running:

```

$ mysqladmin --user=<username> -p status

```

As for PHP, easiest thing to do I guess is to write a very simple PHP page, and see if it loads properly (i.e. Apache recognises .php, and invokes the php interpreter accordingly).

---

### Post by bettlebrox on 2006-11-28
Have a look at the [The Linux System Administrator's Guidel]("http://www.tldp.org/LDP/sag/html/index.html")

Plus, load of other useful docs at [Debian's]("http://www.us.debian.org/doc/") site;

---

### Post by scrooge_74 on 2006-11-28
> **bettlebrox said:**
> Have a look at the [The Linux System Administrator's Guidel]("http://www.tldp.org/LDP/sag/html/index.html")

Plus, load of other useful docs at [Debian's]("http://www.us.debian.org/doc/") site;

I originally started with Debian and then moved onto UBUNTU, I think it was a good learning experience doing it this way.

---

### Post by Bill007 on 2006-11-29
some how I dont think Apache2 or Mysql where loaded in the install
I chose Lamp server option aswell. Some how the lamp part of server didnt get installed any ideas

** apache2ctl status**

bill007@production:~$ apache2ctl status
-bash: apache2ctl: command not found
bill007@production:~$
[B]
ps -A | grep apache[/B]

bill007@production:~$ ps -A | grep apache
bill007@production:~$

bill007@production:~$ sudo /etc/init.d/apache2 start
sudo: /etc/init.d/apache2: command not found
bill007@production:~$


bill007@production:~$ sudo apt-get install apache2
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bill007@production:~$


Cant seem to find the files either


Oh and thaks for all those replies good info

---

### Post by reclusivemonkey on 2006-11-29
Another useful resource is 

[http://rute.2038bug.com/rute.html.gz](http://rute.2038bug.com/rute.html.gz)

---

### Post by az on 2006-11-29
Here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

And also perhaps this:

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

