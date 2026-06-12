---
title: "Killed X server - how to disable X at boot"
date: 2007-09-20
forum: General Help
---

### Post by caen1944 on 2007-09-20
Hi Folks,

I did something silly on the ubuntu system that I set up as a samba server for my office at work. 

Here is the problem: I installed ubuntu 7.04 desktop when I had the computer hooked up to my desktop 21 inch dell monitor. Everything worked great. Then when I moved the computer to another room, with a crappy little monitor, the x server resolution/video quality was horrible When I got poor video resolution on my home computer I followed the instructions in [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

and everything worked great. I ran the autodetect script on my work computer, and following that, it hangs when it tries to start x. Linux is up and running under the surface, I can telnet in over the network, samba is working, etc,  but that doesn't make me feel so good (what if i have network problems for instance)

I can live without X windows, but I need to at least login from the terminal. 

How can I configure X not to start at bootup, and present me with a terminal login prompt instead?

Any ideas........

Thanks so much.

---

### Post by yabbadabbadont on 2007-09-20
```
sudo apt-get --purge remove gdm
```
;)

---

### Post by WakkaDojo on 2007-09-20
Did you backup your xorg.conf file? If so, just press Alt+Ctrl+F1 and restore your file from there. You can also restore the xorg.conf file from the terminal if you don't have a backup.

---

### Post by bodhi.zazen on 2007-09-20
> **yabbadabbadont said:**
> ```
sudo apt-get --purge remove gdm
```
;)

LOL, you are cruel :twisted:

System _ Administration -> Services

Scroll down and un-tic "Graphical Login manager"

Also you can manage services from the command line with update-rc.d :

Stop:```
sudo update-rc.d gdm remove
```

Start:```
sudo update-rc.d gdm defaults
```

You can also edit the scripts manually  ...

Also, FYI, you can have more then 1 server lay out for X, one for each monitor.

Last, and easiest of all, you can get to a console with Ctrl-Alt-F1 or Ctrl-alt-F2 (up to Ctrl-alt-F6)

---

### Post by yabbadabbadont on 2007-09-20
I don't see how that was cruel.  The OP stated that he doesn't want a graphical login.  Removing gdm will not remove anything that he needs in this situation.

> **bodhi.zazen said:**
> System _ Administration -> Services

Scroll down and un-tic "Graphical Login manager"
X does not run, hence his post.  ;)

> **bodhi.zazen said:**
> Also you can manage services from the command line with update-rc.d :

Stop:```
sudo update-rc.d gdm remove
```

Start:```
sudo update-rc.d gdm defaults
```

He'll need to use the "-f" parameter with those commands or update-rc.d will refuse to do anything as gdm is still installed.  (and its init script will still be in /etc/init.d)

---

### Post by bodhi.zazen on 2007-09-20
> **yabbadabbadont said:**
> I don't see how that was cruel.  The OP stated that he doesn't want a graphical login.  Removing gdm will not remove anything that he needs in this situation.

LOL

> X does not run, hence his post.  ;)

I am not sure he wants to completely remove gdm is all I am saying ...

> He'll need to use the "-f" parameter with those commands or update-rc.d will refuse to do anything as gdm is still installed.  (and its init script will still be in /etc/init.d)

Thank you for that information.

---

### Post by dcstar on 2007-09-20
> **caen1944 said:**
> 
...........
I can live without X windows, but I need to at least login from the terminal. 

How can I configure X not to start at bootup, and present me with a terminal login prompt instead?

Any ideas........

Thanks so much.

Just because you can't see the X screen (probably because of incorrect Res/Refresh settings), doesn't mean that it is not working.

Text logins are already available if you just press CTRL-ALT-F1 through to F7, and you can just disable the GDM as per the previous instructions (probably better to just fix the res issue, though).

---

### Post by caen1944 on 2007-09-21
Thanks,

I forgot about the Alt-F1 thing. I used to use that a bunch the that last time I used Linux 15 years ago with the slackware distribution. Getting the X-server to work then was a real treat....

Thanks for the help. I'm good now. I don't really want the x-server anyway now that the system is "in production" so to speak, but it was really useful having when I was re-familiarizing myself with linux and ubuntu.

By the way, once I am logged in on the console, do I still use "startx" to fire up x windows or do I need something more fancy to get the gnome interface working?

Thanks for your help.

---

### Post by yabbadabbadont on 2007-09-21
There should be a file called, gnome.desktop in /usr/share/xsession(s?).  Inside that text file there will be a line that starts with "Exec="  (or something close to that).  You can call the same program as in that Exec line in your ~/.xinitrc file (You'll need to create it).  Then startx should launch Gnome for you.

---

