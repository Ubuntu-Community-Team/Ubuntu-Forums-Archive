---
title: "linux getting slow"
date: 2007-01-17
forum: General Help
---

### Post by vidak on 2007-01-17
I have the following problem: I bought my laptop for about a year. I've installed Breezy on it, and updated for Edgy as soon as possible. The laptop is not _that_ old one, however its getting slow... Could this caused by the lots of packages installed? Could anybody manage to make a machine faster in a situation like that without reinstalling the whole system? 

Thanks for your help!

---

### Post by Richard Kut on 2007-01-17
Hello! First off, do this:

sudo apt-get update

Depending on how far behind you are in your updates, this could fix some of the issues.

Also, you are not being specific in the description of your hardware and software, and how you are using those. This will greatly influence any kind of advice that I or any of the other forum members will offer you. Please consider updating your post with the above details.

Failing that, here is what I would do to start:

1 - Check which processes are running, and how much juice they each consume. Start evaluating each one to see if it is needed or not. If not, then stop it and disable it so that it does not autostart the next time that you boot.

2 - Remove any software, using Synaptic or whatever other tool that you are comfortable with, which you do not need. Example: maybe your laptop does not have BlueTooth, but the bluez* software is running anyway. That would be a candidate to rip out by the roots.

and possibly

3 - See if you are swapping to disk. If so, maybe you have a defective RAM chip, and now you don't have enough memory anymore?

The above is a quick and short list of what could easily be done.

I hope that this helps to get you started. Good luck!

---

### Post by Jussi Kukkonen on 2007-01-17
> Could this caused by the lots of packages installed? 
Yes, if they are daemons (services). You could paste the output of this command here:
```
 ls /etc/rc2.d/
```
Then we'll see what you have running...

Also you could check free space with ***df***

---

### Post by vidak on 2007-01-18
The updating is done almost every day, when something new comes out...
I'm using KDE, which eats a lot of memory, and the swapping occurs typically when running programs like OpenOffice... But firefox seems also to get slowed...
The current configuration is a laptop with a 1.6GHz Pentium M processor, and 512megs of memory. the swap space is one Gb. The free space is about 1.2-1.5Gb on the system partition (of about 8-9Gb total)
There are _really_ much packages, around 250,000 files, or even more, because I use some programs which have to be compiled, and there are a lot of developement packages also, which ones I tried to eliminate, but there are still a lot left... 
when I'll be from that laptop, I'll paste the content of rc2.d too... 
Thanx for trying to help... :)

---

### Post by vidak on 2007-01-20
> **Jussi Kukkonen said:**
> Yes, if they are daemons (services). You could paste the output of this command here:
```
 ls /etc/rc2.d/
```
Then we'll see what you have running...

Also you could check free space with ***df***

content of rc2.d:

README              S19cupsys             S20nethack-common  S89atd
S05vbesave          S20apmd               S20nvidia-kernel   S89cron
S10acpid            S20apt-index-watcher  S20powernowd       S91apache2
S10powernowd.early  S20dbus               S20rsync           S98usplash
S10sysklogd         S20exim4              S20samba           S99acpi-support
S11klogd            S20hotkey-setup       S20ssh             S99rc.local
S12sl-modem-daemon  S20inetd              S25bluetooth       S99rmnologin
S13kdm              S20kde-guidance       S25mdadm           S99stop-readahead
S14ppp              S20laptop-mode        S50proftpd
S18hplip            S20makedev            S89anacron

free space:
/dev/hda3             8,9G  7,3G  1,2G  87% /

---

### Post by happy-and-lost on 2007-01-20
[http://www.ubuntuforums.org/showthread.php?p=1255511](http://www.ubuntuforums.org/showthread.php?p=1255511) but be careful ;)

---

### Post by vidak on 2007-01-21
> **happy-and-lost said:**
> [http://www.ubuntuforums.org/showthread.php?p=1255511](http://www.ubuntuforums.org/showthread.php?p=1255511) but be careful ;)

took a look around /var, and deleted 2Gb of trash (downloaded packages, etc), which made at least aptitude faster... Installed swiftfox also, and stopped nvidia-kernel daemon (why is it there? I got an i915 card...)
I am thinking about making an own kernel again, but it's a lot of work... and usually I have to do it at least 3 times to get a correct one :(

Thanks for help, anyway...

---

