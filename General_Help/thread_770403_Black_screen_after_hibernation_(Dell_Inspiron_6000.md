---
title: "Black screen after hibernation (Dell Inspiron 6000)"
date: 2008-04-27
forum: General Help
---

### Post by djst on 2008-04-27
I upgraded to 8.04 today and not the computer can't resume from hibernation correctly. The screen remains blank (but the computer can actually be used, e.g. I can hit Ctrl+Alt+F1, login, type shutdown -r now and hit enter, and the computer actually restarts).

It worked perfectly on 7.10. Any ideas? My computer is a Dell Inspiron 6000.

---

### Post by ghost_ryder35 on 2008-04-27
how big is your /swap?  if its to small it can not write all the necessary information to that partition and hibernation uses it.  you could also check the power settings under system, administration, power managment :)  possibly a bad upgrade though, have been hearing horror stories all week.....

---

### Post by djst on 2008-04-27
I don't know how to tell the size of it, but I'm pretty sure that's not the issue since it's been working perfectly before, and really hibernation itself works fine -- the part that's not working is litting up the screen again.

---

### Post by ghost_ryder35 on 2008-04-27
you can use 
```

top

```
or system monitor to see the size of /swap
 
Next time this happens how bout you post your messages.log so we can have a little look at whats going on
 
```

cp /var/log/messages.log /home/yourname/Desktop

```

---

### Post by strabes on 2008-04-27
What video card do you have? Which drivers are you using?

---

### Post by tamias on 2008-04-28
I have logged the same problem, on another Inspiron 6000, at [http://ubuntuforums.org/showthread.php?p=4788709](http://ubuntuforums.org/showthread.php?p=4788709).

(Incidentally, djst, you can recover use of the laptop by typing *sudo vbetool dpms on* at the command line).

The problem is not related to swap space as far as I can tell, but a bug somewhere in GNOME power management.

---

### Post by djst on 2008-05-03
> **strabes said:**
> What video card do you have? Which drivers are you using?

How can I tell?

---

### Post by strabes on 2008-05-03
> How can I tell?

Paste the output of the following two commands (one at a time) in a terminal (Applications > Accessories > Terminal).

```
lspci | grep VGA
fglrxinfo
```

---

### Post by tamias on 2008-05-04
I'm having the same problem as djst, on the same model laptop (see [http://ubuntuforums.org/showthread.php?p=4835280#post4835280](http://ubuntuforums.org/showthread.php?p=4835280#post4835280)). My outputs from these commands are:

```
lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
```

```
fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
```

---

### Post by tamias on 2008-05-13
*bump*

---

### Post by bwphilip on 2008-05-13
on my Dell Inspiron 2650 I needed to turn the backlight off and on with xset dpms force off or xset dpms force on

---

### Post by tamias on 2008-05-27
I seem to have been able to fix this problem by executing

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

The replacement /etc/X11/xorg.conf is very much shorter than the previous version which the dpkg reconfigure replaced: in particular, it contains no information about available screen modes. Yet, it seems to work. I assume something in my older xorg.conf was breaking the DPMS resume.

---

### Post by Pulse214 on 2008-06-03
I have had the same problem with my I6000, i've had it ocasionally on ubuntu (just installed it) but i've had it happen in windows too. my personal feeling is that the problem is either with a power management system (acpi) or, in my case, the lid position switch.  the hinges on the i6000 are crap, mine's about to go in for warranty repair, and i have a feeling the loose hinges are causing issues with the switch for the backlight/screen power.

---

