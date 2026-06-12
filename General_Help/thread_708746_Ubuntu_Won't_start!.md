---
title: "Ubuntu Won't start!?"
date: 2008-02-26
forum: General Help
---

### Post by Bigspice on 2008-02-26
Ubuntu will not start. When I boot my computer the Ubuntu logo comes up and shows that it is loading.  This is the first time this has ever happend to me.  I have been using ubuntu for a couple of months now and then this random thing happened.   After it is done loading it looks like this:

*Starting anac(h)ronistic cron anacron
*Starting deferred execution scheduler atd
Starting periodic command scheduler crond
*Checking batter state...
Running local boot scripts (/etc/rc.local)
Starting timidity
Starting TiMidity++ ALSA midi emulation...


Then it stops and it won't boot.

PLEASE HELP

I have computer science project on it that is due tonight!!

---

### Post by pytheas22 on 2008-02-26
I'm not sure why it's not starting (have you tried several times with the same results?), but if you need to get your project off of it, you can always boot to the live CD and mount your Ubuntu partition in order to get the file.  To do that:
```

sudo mkdir /media/ubuntu
sudo mount /dev/YOUR-UBUNTU-PARTITION /media/ubuntu
```

where YOUR-UBUNTU-PARTITION = the name of your Ubuntu partition, which is probably something like sda1 or sda2.

Then you can cd or browse to /media/ubuntu and be able to access your file system.

I hope this helps, and that someone will be able to help you solve the real problem as well.

---

### Post by Bigspice on 2008-02-26
Hey, thanks.  I already figured out how to get my project off of it.  I was able press Ctrl + Alt + F1 and get a command line and emailed my project to myself through the command line.  The thing that boggles my mind is the fact that it is letting get to my files but it won't start up anything else.  It has never done this before.

---

### Post by pytheas22 on 2008-02-26
If you are able to log in and run applications, then it sounds like your system is booting; it's just unable to start X, the graphical interface.  Did you make any changes to anything related to graphics before the problem began (for instance, were you fiddling with the Screens and Graphics utility)?

Try typing "startx" at the command line; if there's a problem with X, it will probably complain about it.

You could also try to reconfigure X with the command
```

sudo dpkg-reconfigure -phigh xserver-xorg
```

it would be a good idea first to backup your current X configuration, however, just in case this isn't the problem:
```

cp /etc/X11/xorg.conf ~/Desktop/xorg.conf.bak
```

---

