---
title: "Upgrade failed and my system won't boot. Now what?"
date: 2016-05-05
forum: General Help
---

### Post by james214 on 2016-05-05
I was trying to upgrade from 14.04 to 15.04... and it seems to have failed... and now my computer won't boot. So... now what? At a minimum, I would at least like to recover my files. Thankfully, I can boot Ubuntu from a USB flash drive right now. (Is there any way to access my PC's hard drive from this?)

Note:  I'm a totally Linux n00b. I know how to copy and paste into the terminal, but that's about it.

Edit:  Okay, accessing my old files was easy. Is there any way to restore my PC Ubuntu so it will boot... or must I reinstall 14.04 on it using the Flash USB drive? (Is there any way for me to create a 16.04 boot on the USB stick that I am currently using? Or is that asking for trouble?)

---

### Post by howefield on 2016-05-05
How did you do the upgrade to 15.04 (as this is an unsupported version) ?

How did it fail, did the upgrade appear to work and then the pc not reboot or something else ?

---

### Post by james214 on 2016-05-05
I got a notice from Ubuntu telling me I could upgrade. The files started downloading, but I'm not sure what happened after that -- I think I made it like 80% through the entire upgrade process... and I suspect Ubuntu failed at the automatic reboot. I came back to my computer and my screen was totally blank.

---

### Post by Bashing-om on 2016-05-05
james214; Maybe, all good .

In addition to howefield's request ^^, also good to know what we are dealing with:

Let's take a gander.
At the login screen, key combo ctl+alt+F1 to gain a console interface. Can you login here with you credentials ?

If so the next thing is we would want to know the status of the sources :
show us in a pastebin:
```

cat /etc/apt/sources.list | nc termbin.com 9999

```
pass the resulting URL back here and we have a look where you stand.

Maybe all we have here is a failure on your part to revert a proprietary graphics driver, and now in the upgrade that graphic's driver is broke .

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by james214 on 2016-05-05
I don't get a login screen -- the screen just goes blank. But after it booted to the blank screen, I was about to get to the console screen and login. This brought me to a Terminal prompt, it seems. I entered what you said to enter. Here is what it returned:

nc: getaddrinfo: Temporary failure in name resolution

---

### Post by Bashing-om on 2016-05-05
james214; Ouch ... 

No networking enabled .
Can you, from the grub boot menu, boot a recovery kernel and in this recovery console choose ' enable networking' ?

what returns:
```

ping -c3 ubuntu.com

```
do you see:
> 
--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002m



[INDENT][INDENT]what we have here is a failure to communicate
[/INDENT][/INDENT]

---

### Post by james214 on 2016-05-05
I don't know what a recovery kernel is... but I did reboot my PC and then used "Ctrl + Alt + F1" to get to a command prompt. When I entered "ping -c3 ubuntu.com", I received a message to the effect of: "unknown host ubuntu.com".

---

### Post by oldrocker99 on 2016-05-05
It certainly appears that you have no networking. Can you attach an Ethernet cable and try again? **Some** wireless chips have problems with Linux, and some work right out of the box.

---

### Post by james214 on 2016-05-05
I have an ethernet cable attached (though it's plugged into my USB port -- I don't have an ethernet port). My networking works just fine when I boot from the USB flash drive.

---

### Post by Bashing-om on 2016-05-05
james214; Welp:
this:
> 
When I entered "ping -c3 ubuntu.com", I received a message to the effect of: "unknown host ubuntu.com".

says you have a problem. If you can not talk to ubuntu.com for sure you can not update your system.
So what can you talk to ?
what returns:
```

ping -c3 8.8.8.8

``` and we see in what direction we work to .

[INDENT][INDENT]what we have here is a failure to communicate
[/INDENT][/INDENT]

---

### Post by james214 on 2016-05-05
*ping -c3 8.8.8.8* returned something along the lines of "*no network detected*"

---

### Post by Bashing-om on 2016-05-05
james214; Well well ...not

Can not get out of house.
Next is do we have an operational network Interface card ?
What returns:
```

ping -c3 127.0.0.1

```

[INDENT][INDENT]see where we go from here
[/INDENT][/INDENT]

---

### Post by james214 on 2016-05-05
*ping -c3 127.0.0.1 *returns *ping: icmp open socket: operation not permitted*

---

### Post by Bashing-om on 2016-05-05
james214; Yuk;

Houston, we have a problem.

OK, square one, hardware:
Post back the out-puts  -- Between Code Tags -- of terminal commands:
```

sudo lshw -C network
lspci | grep Ethernet
ip link ls
ls /sys/class/net

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Are you attempting to connect wired or WIFI ?

[INDENT][INDENT]it is a thing
[/INDENT][/INDENT]

---

### Post by james214 on 2016-05-06
This is about the best I can do. You should be able to read the outputs if you zoom.  (Click to zoom).

[http://i.imgur.com/tFE8L4l.jpg](http://i.imgur.com/tFE8L4l.jpg)
[http://i.imgur.com/CQFs3Zs.jpg](http://i.imgur.com/CQFs3Zs.jpg)

---

### Post by Bashing-om on 2016-05-06
james214; Well !

Broadcom. the good thing is that there is help.
the bad is that you have to configure the driver.
Help with Broadcom bcm43xx can be found at :
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

[INDENT][INDENT]and then we continue on
[/INDENT][/INDENT]

---

