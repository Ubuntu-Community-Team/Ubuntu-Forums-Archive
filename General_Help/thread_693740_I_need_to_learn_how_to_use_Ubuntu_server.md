---
title: "I need to learn how to use Ubuntu server"
date: 2008-02-11
forum: General Help
---

### Post by ayet on 2008-02-11
I need to learn how to use Ubuntu server, please provide me any documentations on how to use it.

what I downloaded was the Ubuntu 6.06 LTS - Supported to 2011, since its not in GUI how do you use it?

---

### Post by aeiah on 2008-02-11
you use the CLI, since it hasnt got a GUI. what are you wanting to use it for?

---

### Post by apetresc on 2008-02-11
[This link](https://help.ubuntu.com/ubuntu/serverguide/C/index.html) probably contains just about everything you want to know. Enjoy :)

---

### Post by ayet on 2008-02-11
I need to setup a server much like what windows 2k server can do, like setting users from ubuntu clients etc, the common stuffs, is there a pdf files on how to learn the basic stuff.

---

### Post by ayet on 2008-02-11
> **AdrianP said:**
> [This link](https://help.ubuntu.com/ubuntu/serverguide/C/index.html) probably contains just about everything you want to know. Enjoy :)

tnks will read this.

---

### Post by aeiah on 2008-02-11
that link should give you plenty of information. if you are finding the CLI too daunting, you could install the ubuntu gnome desktop (or kde, xfce etc) on top of the server. you can always elect not to run it on startup once they server is set up.

---

### Post by ayet on 2008-02-11
can you do that? have a GUI on ubuntu server?

---

### Post by apetresc on 2008-02-11
> **ayet said:**
> can you do that? have a GUI on ubuntu server?

Yes, of course, it's just not there by default. Just install it through apt-get, use it to set everything up, then remove gdm from the default runlevel once everything is set up and you're ready for the server to be in production. The desktop install will only be taking up a small amount of space, nothing more. It's a good compromise for beginners.

---

### Post by ayet on 2008-02-11
Iam really new to this but how do you?
1. install it through apt-get
2. remove gdm from the default runlevel

---

### Post by ayet on 2008-02-25
I Google this one 


> How to Install XWindows and GNOME Window Manager on Ubuntu Server (6.06.1 LTS)
Ubuntu Server does not install XWindows or the GNOME window manager by default.

To install GNOME, you have two options:
1.    Install just XOrg (XWindows) and the base GNOME desktop environment.
2.    Install the entire Ubuntu Desktop Environment (this includes applications such as OpenOffice, etc.)

In most server applications, the first option is all you will ever need and, at least in Dapper (6.06.1), it will take approximately 650MB of additional hard disk space.

4 Steps to Install XOrg and GNOME:
Note: This will retain your server's default of booting to console/terminal logon

1.   Uncomment the "universe" repositories in sources.list:
   $ vi /etc/apt/sources.list
   $ apt-get update 
 
2.    Install the packages:
   $ apt-get install x-window-system-core xserver-xorg gnome-desktop-environment

3.    Configure XOrg:
       (Select default options if uncertain)
   $ dpkg-reconfigure xserver-xorg
 
4.    Remove gdm from the Default Runlevel:
       Because XOrg adds gdm to the server's default runlevel, the server will automatically boot to a graphical login prompt; this step will remove gdm from the default runlevel and retain Ubuntu Server's default text logon prompt.  Install rcconf (Debian Runlevel configuration tool) first to edit the default runlevel.  See man rcconf after installing for more information.

   $ apt-get install rcconf
   $ rcconf
   Scroll to [*] gdm and remove the check by pressing the spacebar.
      Submit your changes by press Enter.
 
5.    Reboot to test:
   $ shutdown -r now

3 Steps to Install the entire Ubuntu Desktop Environment:
WARNING: This will configure your server to boot to graphical logon

1.   Uncomment the "universe" repositories in sources.list:
   $ vi /etc/apt/sources.list
   $ apt-get update
 
2.    Install the packages:
   $ apt-get install ubuntu-desktop
   $ apt-get install gdm
   $ /etc/init.d/gdm start
   $ dpkg-reconfigure xserver-xorg
 
2.    Configure XOrg
   $ apt-get dpkg-reconfigure xserver-xorg


do you just type this onthe console?

```
   $ vi /etc/apt/sources.list
   $ apt-get update 
```

---

### Post by ayet on 2008-02-25
or just

sudo apt-get install ubuntu-desktop

---

