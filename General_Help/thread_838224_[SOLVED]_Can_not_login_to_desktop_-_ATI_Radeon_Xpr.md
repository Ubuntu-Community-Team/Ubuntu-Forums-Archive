---
title: "[SOLVED] Can not login to desktop - ATI Radeon Xpress 200"
date: 2008-06-23
forum: General Help
---

### Post by rampageoberon on 2008-06-23
Hi,

I installed the ubuntu desktop 8.04 on a friends desktop but I can't login properly. It seems to log in at first and then kills X and returns me to the login screen.

Not sure how to go about this. Please help

---

### Post by dracayr on 2008-06-23
press Ctrl+Alt+F1 and see if you can login there. You might want to try recovery mode and "Repair X server"

dracayr

---

### Post by rampageoberon on 2008-06-23
I can't get into any of the tty's bar tty7. I've tried the fix xserver but it doesn't seem to work too.

---

### Post by danwood76 on 2008-06-23
Is this a completely clean install or have you done anything to it?
If its clean I would try a reinstall, check that the CD media is good from the boot menu on the live CD also.

---

### Post by rampageoberon on 2008-06-23
Its a completely clean install. So not even had a chance to change the drivers if thats what it needs

---

### Post by danwood76 on 2008-06-23
You may not need to change the drivers but you may have a duff install CD, its worth checking the disk for errors and trying a reinstall.

Also I'm running a laptop with a Xpress 200M and it worked perfectly from the first install so I very much doubt that this is your problem.

---

### Post by rampageoberon on 2008-06-23
I've installed from the same CD onto my laptop (intel card) and its worked fine. I tried a 64bit cd and 32bit one too and same error. Is it worth trying a different CD?

---

### Post by danwood76 on 2008-06-23
I would use the CD test utility that you can choose from the initial boot menu from the live CD, that will tell you if the CD is OK.

If the CD is ok I would say that another piece of hardware is causing the issue.

RUn this command in the terminal of the Live CD to determine what hardware you have (and please post it)
```

sudo lspci -v

```

---

### Post by rampageoberon on 2008-06-23
The Live CD won't even log in. I've checked that it has no defects.

I get the same issue as when i install. It seems to login and then returns back to the login screen everytime.

Edit: I can't even use any of the other tty's

---

### Post by danwood76 on 2008-06-23
Wait a second, so how have you managed to install it?
Or havent you?

If you havent you probably need the alternative install CD, it gives a text based install as opposed to the graphical one but still gives all the same install options and so on.

---

### Post by rampageoberon on 2008-06-23
I installed it from the live cd, but selected the install option instead of booting into the live cd (at the boot menu) and it seemed to install fine.

I could try the alternative cd if necessary.

---

### Post by rampageoberon on 2008-06-23
Sorry if I was not clear before. I booted the computer with the live CD and at the boot menu did not choose the first option which was try ubuntu without changing any settings.

Instead I selected Install Ubuntu and proceeded to install it on a spare partition. (I guess thats how the alternative install is, though this was not text based, there was a proper gui).

It seems to load up fine after, just won't let me use any terminals or boot in to the actual system (Desktop or terminal). Hope that is better and someone can help with this.

---

### Post by danwood76 on 2008-06-23
Ok I see.

There must be an issue with some piece of hardware on the system, check for X errors.

First boot into recovery mode by pressing escape at the grub menu and selecting recovery mode.
Once logged into recovery mode run the following command, make sure you get the case correct:
```

cat /var/log/Xorg.0.log | grep '(EE)'
cat /var/log/Xorg.0.log.old | grep '(EE)'

```
Hopefully one of these will display a command which will give us something to go on.

Another thing you could try is setting X to use the vesa drivers which should work with all systems.

To do this boot in recovery mode as above and edit the xorg.conf
```

nano /etc/X11/xorg.conf

```
Look for a "Device" section that has Video Device in its description and change the 'Driver' line to be "vesa".

So on mine it would be something like this after the edit:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

```
Save that and reboot to see if it then loads

---

### Post by rampageoberon on 2008-06-23
Thanks for that guide. The only output from both log files of xorg is as follows.

```
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
```

I tried changing the xorg.conf file and the screen doesn't respond at all after grub. I just get a blank screen :(

---

### Post by CaKiwi on 2008-06-23
I had the same prolem. See

[http://ubuntuforums.org/showthread.php?t=830531&page=2](http://ubuntuforums.org/showthread.php?t=830531&page=2)

I solved it by changing my session to failsafe Gnmome and then logging in. Once I was logged in I went to  System->Administration->Hardware drivers  and intalled the proprietry ATI driver

---

### Post by CaKiwi on 2008-06-23
I had the same problem. See

[http://ubuntuforums.org/showthread.php?t=830531&page=2](http://ubuntuforums.org/showthread.php?t=830531&page=2)

I solved it by changing my session to failsafe Gnome and then logging in. Once I was logged in I went to  System->Administration->Hardware drivers  and installed the proprietary ATI driver.

---

### Post by rampageoberon on 2008-06-23
Yes that worked perfectly. Thanks so much for all the help.

---

