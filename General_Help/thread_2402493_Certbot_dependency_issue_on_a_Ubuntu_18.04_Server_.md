---
title: "Certbot dependency issue on a Ubuntu 18.04 Server edition OS"
date: 2018-10-01
forum: General Help
---

### Post by jsbtdx on 2018-10-01
:~$ sudo apt-get install python-certbot-apache
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 python-certbot-apache : Depends: python3-certbot-apache but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I'm trying to install certbot onto my server to tie into my Webmin. 
I have mySQL, PHP, and Apache2 installed currently.
Webmin is not installed yet.

I've tried: sudo apt-get install -f and nothing happens

---

### Post by dgibson74 on 2018-11-26
[COLOR=#868686][FONT=&quot]This fixed it for me...


sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install python-certbot-apache

good luck!
[/FONT][/COLOR]

---

