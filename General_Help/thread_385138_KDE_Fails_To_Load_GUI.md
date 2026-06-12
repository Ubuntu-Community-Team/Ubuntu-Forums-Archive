---
title: "KDE Fails To Load GUI"
date: 2007-03-15
forum: General Help
---

### Post by burkezillar on 2007-03-15
Hey guys, this is my first post here. Hello!

I installed Ubuntu 6.06 Tuesday night. I then installed KDE onto it, and then tried to install Beryl, without success. Then after I switched users to go into root, the power died. And then everytime I started up Ubuntu (Or Kubuntu), it'd hang when it'd load up. 

I then reinstalled Ubuntu 6.06 again, but this time I done an online upgrade to 6.10, and then went to reinstall KDE. Everything worked.

I then tried Beryl again, I updated the nVidia drivers, and they worked. I rebooted the machine after this just to make sure. It did work. I then completed the Beryl installation, but alarms bells started to ring when KDE failed to start, and I was left at the command prompt. I typed in sudo /etc/init.d/kdm start... and it said that KDE was already running. I stopped KDE, then restarted it. And it worked. I rebooted, and still the same command prompt comes up. Starting and stopping KDE didn't work this time.

I don't know why it's doing this. I followed the instructions right down to the letter. I was using the tutorial on this page:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia")

I think, this line maybe the cause of the problems, as it was written to the KDE start up file:

***ln -s /usr/bin/beryl-manager ~/.kde/Autostart/beryl-manager***

Does anyone know whats gone wrong here? I would reinstall Ubuntu but I just got Beryl working, and I want to know whats happened.

Thank you for your time!

---

### Post by Waappu on 2007-03-15
Hi

Try to remove Beryl from startup programs and see if system starts normaly. Type in terminal ```
rm ~/.kde/Autostart/beryl-manager
```

If systems starts ok, then try run beryl manually from terminal ```
beryl-manager
```
it might give some error messages that helps find out what is problem

---

### Post by burkezillar on 2007-03-15
I removed that line, but nothing happens. It still goes to the command prompt.

I have tried the following command:

sudo startkde

And it has thrown up some errors:

[I]xsetroot: unable to open display ' '
xset: unable to open display
xsetroot: unable to open display ' '
startkde: Starting up...
ksplash: cannot connect to X server
xprop: unable to open display ' '
usage: xprop [-options ...] [[format [dformat]] atom] ...

(command options listed)

startkde: Shutting down...
Warning: connect() failed: : No such file or directory
Error: Can't contact kdeinit!
startkde: Running shutdown scripts...
xprop: unable to open display ''
usage: xprop xprop [-options ...] [[format [dformat]] atom] ...

(command options listed)

startkde: Done.
mick@home-linux:~$[/I]

I'm not an experienced Linux user... but I think the X Server or KDE.. or both may have been deleted?

---

### Post by Waappu on 2007-03-15
Hi

If you type ```
startx
```

---

### Post by burkezillar on 2007-03-15
I just googled how to reinstall KDE, and I looked at their documentation. It comes up with:

startkde fails with can not connect to X server. What is wrong?

So I read it, and it says I should type startx first. I do so, and get the following error:

Fauked to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly. Please consult the NVIDIA README for details.

Fatal server error:
no screens found
XIO: fatail IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) 0 events remaining.

I'm gonna try to reinstall the nVidia drivers again.

---

### Post by Waappu on 2007-03-15
Hi

Envy is great tool for install nvidia drivers
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by feest on 2007-03-15
log in as root in the terminal (the only option since you don't have x) 

su
<password>

change dir to /etc/X11
cd /etc/X11

apply the xorg.conf backup file
cp xorg.conf.backup xorg.conf

does this help you?

---

