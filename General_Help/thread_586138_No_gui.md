---
title: "No gui"
date: 2007-10-22
forum: General Help
---

### Post by Calicoo on 2007-10-22
Problem: (EE) AIGLX: Screen 0 is not DRI capable.

I installed Gutsy Gibbon 64 from the alt cd because the live cd wouldn't load a gui (Don't know why; 2 GB Ram, AMD64 3700+, eGeForce 7600 GT). Anyway, all I get is a command prompt. I can log in but from there I'm lost. If I ctrl + alt F7 it just brings up a blank screen. I'm including links to my xorg.0.log and xorg.conf files. One thing I did notice was that it shows my second graphics card (the 6800 GS) instead of the 7600 GT that's connected to the monitor.

I did have Feisty on here and it installed fine from the live cd so I really don't know why Gutsy isn't letting me have a gui. All help is appreciated.

[http://pastebin.com/m380daaa0](http://pastebin.com/m380daaa0)

[http://pastebin.com/mdab0d1](http://pastebin.com/mdab0d1)

Thanks,
Eric

---

### Post by Sockerdrickan on 2007-10-22
I'm also having troubles with that. If I were you I would go with 7.04

---

### Post by mahousaru on 2007-10-22
The splash screen might be killing the display device.

When you boot edit the boot line and change splash to nosplash=y

You might still get a black screen so when everything has settled down, you need to hit enter and then type startx followed by enter.

---

### Post by Calicoo on 2007-10-22
[QUOTE=Tux0r]I'm also having troubles with that. If I were you I would go with 7.04[/QUOTE]

I should've worded my statement better. When I first installed 7.04 it went fine (live cd worked, gui). But after I uninstalled it and tried installing 7.10 I get that screen. I thought maybe it was just the cd so I tried installing 7.04 again and no gui for the live cd comes up for it either.

[QUOTE=mahousaru] The splash screen might be killing the display device.

When you boot edit the boot line and change splash to nosplash=y

You might still get a black screen so when everything has settled down, you need to hit enter and then type startx followed by enter.[/QUOTE]

I'll have to try that in a couple hours.

I should also note that I do hear the system start chime and the log in chime after I log in (even though I can't see anything) on the ctrl + alt + F7 screen.

---

### Post by Calicoo on 2007-10-22
I tried nosplash=y but my problem still persists. I actually do see the splash screen, but after it loads all the way is when it goes blank.

---

### Post by mahousaru on 2007-10-22
*scratches head*
try adding as well as nosplash=y (actually change splash to that) 
vga=771
for 800x6002x56 or
vga=773
for 1024x768x256

How about giving the alt installer a go?  The live cd hates my laptop, and my display crashes most of the time during boot if i dont set vga=771 and nosplash=y with it.  But once I've installed it, it is fine.

---

### Post by Calicoo on 2007-10-24
I added vga=773 and all that did was make the screen blank. Didn't even see a command prompt.

I went into recovery mode and did a startx and it gave me this warning:

(WW) NV: No matching Device section for instance (BusID PCI:5:0:0) found.

---

### Post by commonlyUNIQU3 on 2007-10-24
You might try to run the following command to start with a clean xorg.conf file:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This command can be found in a commented out line of your /etc/X11/xorg.conf file...  If you want to view the command there, and you are stuck in bash land you can try the following:

```
nano /etc/X11/xorg.conf
```

That will let you view the contents of your xorg.conf file - which is most likely the root cause of your problem.

That should be a good starting point at least....

---

### Post by Calicoo on 2007-10-24
Reconfiguring did nothing. :(

Here's my xorg.conf file. I've highlighted some lines that may lead you to some ideas. It shows PCI:4:0:0 when the warning gave me PCI:5:0:0. It also shows my 6800 card instead of my 7600 card. Is is just a matter of editing the file?

[http://pastebin.com/m6ad27918](http://pastebin.com/m6ad27918)

---

### Post by Calicoo on 2007-10-25
Bump.

---

### Post by bodhi.zazen on 2007-10-25
> **Tux0r said:**
> I'm also having troubles with that. If I were you I would go with 7.04

NICE AVATAR !!!!

---

### Post by Calicoo on 2007-10-26
Bump.

---

### Post by Calicoo on 2007-10-27
No one?

---

### Post by mahousaru on 2007-10-28
After hearing the chime have u tried switching to another tty by using

crtl alt f1

Hopefully this wll bring up the command line so you can login via the cli then check

/var/log/messages

and 

/var/log/Xorg.0.log

For any error messages

---

### Post by Calicoo on 2007-10-31
I've posted my xorg.0.log (That I got from within Windows) on the first post. Will it make a difference if I bring it up in the cli of ubuntu?

I'll have to try it tomorrow anyway as it's late here.

---

### Post by Calicoo on 2007-11-14
Sorry it's been a couple weeks. School, work, and life got in the way. Anyway, those are the files you requested. The messages one had to be broken in two because it was too big to be hosted all in one file.

Xorg:
[http://pastebin.com/m1aef4d8a](http://pastebin.com/m1aef4d8a)

Messages:
[http://pastebin.com/m5d739bde](http://pastebin.com/m5d739bde)
 [http://pastebin.com/m6c46b1f4](http://pastebin.com/m6c46b1f4)

---

### Post by Calicoo on 2007-11-17
Bump

---

### Post by Calicoo on 2007-11-18
Bump

---

### Post by Calicoo on 2007-11-19
Bump.

---

