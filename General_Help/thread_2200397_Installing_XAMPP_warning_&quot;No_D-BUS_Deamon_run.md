---
title: "Installing XAMPP: warning &quot;No D-BUS Deamon running&quot;."
date: 2014-01-19
forum: General Help
---

### Post by Janno2 on 2014-01-19
I installed XAMPP-Linux, usig the instructions given on Apache Friends ([www.apachefriends.org/en/xampp-linux.html](www.apachefriends.org/en/xampp-linux.html))
Got the warning: No D-Bus Deamon running.
When I go to [http://localhost](http://localhost) I get the message "It works! This is the default web page for this server. The web server software is running 
but no content has been added yet".
So I opened a terminal, and typed in sudo /opt/lampp/lampp start. Got back:
Starting Xampp for linux 1.8.2-3...
XAMPP: Starting Apache ...fail
XAMPP: Another web server is already running.
XAMPP: Starting MySQL...ok
XAMPP: Starting ProFTPD...ok

Well, almost OK. How to solve the problem?

---

### Post by Lars Noodén on 2014-01-19
The easy way would be to remove XAMPP and use Ubuntu's own tools to install the needed packages instead.  You can install a regular LAMP stack this way:

```

sudo apt-get update
sudo apt-get install lamp-server^

```

Mind the caret in the package name, it is needed.  

Several of the advantages of doing it the Linux way using APT (the package manager) include automatically starting the daemons when the machine is booted, automatic management of dependencies during installation, and automatic tracking of updates including security updates.  Further, doing it using the package manager will ensure that all the programs and data end up in the right, standard places with no duplicates.

---

### Post by RedComputer on 2014-01-19
> **Janno2 said:**
> I installed XAMPP-Linux, usig the instructions given on Apache Friends ([www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html"))
Got the warning: No D-Bus Deamon running.
When I go to [http://localhost](http://localhost) I get the message "It works! This is the default web page for this server. The web server software is running 
but no content has been added yet".
So I opened a terminal, and typed in sudo /opt/lampp/lampp start. Got back:
Starting Xampp for linux 1.8.2-3...
XAMPP: Starting Apache ...fail
XAMPP: Another web server is already running.
XAMPP: Starting MySQL...ok
XAMPP: Starting ProFTPD...ok

Well, almost OK. How to solve the problem?

Apache seems launched as regular program instead of service. Try restarting your computer.

---

