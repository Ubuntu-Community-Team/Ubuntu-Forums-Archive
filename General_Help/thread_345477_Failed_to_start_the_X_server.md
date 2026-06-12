---
title: "Failed to start the X server"
date: 2007-01-24
forum: General Help
---

### Post by suessw on 2007-01-24
Hello

i installed ubuntu server Kernel 2.6.15-26 (LAMP version), which works fine.
After that I was missing the GDM interface, which helps me a lot to manage
the system.

so I login as user and switch over to root.
started sudo apt-get install gmd

which work also fine after I reboot the system. 
After this I getting the following error:

Failed to start the X server (your graphical inface). It ios likely that it is not
set up correctly. diagnose the problem ->

x: cannot stat /etc/X11/X (no such file or directory), aborting

What has to be done or I did wrong???

My be someone can help me out with this issue.


Thx
Wolfgang

---

### Post by Ramses de Norre on 2007-01-24
```
sudo aptitude install xserver-xorg-core gnome-core
```

---

### Post by suessw on 2007-01-24
thx for answering the question. 

However it didn't work for me still getting the same error.
Even I installed the system once again.
I run the command you wrote. It work but the is no change.

What do you suggestion. 

Thx

---

### Post by Ramses de Norre on 2007-01-24
It still says the X11 directory is missing? That should be created when you install xserver-xorg-core... Can you run **sudo dpkg-reconfigure -phigh xserver-xorg** ?

---

### Post by suessw on 2007-01-25
I tried you command. The installation program said : (usr/sbin/dpky-reconfigure: xserver-xorg not installed

thx

---

### Post by Ramses de Norre on 2007-01-25
And you have installed xserver-xorg-core??? That's quite a contradiction...

---

### Post by suessw on 2007-01-25
yes I run 
sudo aptitude install xserver-xorg-core gnome-core

at the end there were a couple of msg which meant x-server will run when it
is configure right

---

### Post by suessw on 2007-01-25
ok 
I run apt-get install xserver-xorg and had also got an option to select
screen option which I seleted 1024x768.

After it I reboot and got the following error

X Window System Version 7,11
Release Date 12. May 2006
X Protcol Version 11, Revision 0, Relase 7.1.1
Build Operating System Linux 2.6.15.7 i686
Current IOperation System: Linux localhost 2.6.17-10-server 4 2 SMP Fri Oct 13.

I wondering I download i386 server version to be sure have it make all right.
why it say above i686?

thx
wolfgang

---

### Post by suessw on 2007-01-29
Here are mine fixes:

I was not able to use unbuntu server. It always showed the error with /etc/X11/x.
Also i tried a couple other video card. I also installed xserver-xorg and run the
dpkp-reconfig -phigh xserver-xorg.

So I downloaded i386 alternate and I did not had any problems. 

This solution work fine for me and I was able to install mysql and php5
as well.

My be this anyone who has the same problem

---

