---
title: "Turn off Screensaver via CLI"
date: 2008-03-09
forum: General Help
---

### Post by ErusGuleilmus on 2008-03-09
Hello,

How would I go about turning off the screensaver permenantly from Terminal?

Thank you for your help.

-Erus

---

### Post by soldats on 2008-03-10
maybe this will work. most monitors use DPMS for power management so you may be able to turn it off this way.
```
sudo xset -dpms
```
if not there is more info via
```
man xset
```
optionally if this doesnt work you can edit the xorg.conf file manually and add some lines under the serverflags section.
```
man xorg.conf
```
if you scroll down youll see where it states how and where to add the lines
ie.
BlankTime
OffTime
SleepTime
SuspendTime
and corresponding values

---

### Post by rkj90266 on 2008-03-16
Well I thank soldats too.  He also pointed out that the name of the gnome screensaver is "gnome-screensaver" (obviously enough).  So I just found the process and killed it by typing (in a terminal):
ps -A
and finding the process id of gnome-screensaver, then 
kill <pid>
The advice is still appropriate - don't type things you don't understand in the terminal, but if you're ok with that, I think this will work. not sure what will happen next time I reboot.

---

### Post by spupy on 2008-03-16
You can consolidate the two commands in one:
```
killall gnome-screensaver
```
But can't you set the screensaver options for something like 99999 minutes, so it wont bother you.

---

### Post by ErusGuleilmus on 2008-03-19
I couldn’t just delay the screensaver time because when I would go into the screen saver menu, it would freeze just as if I had gone into the screensaver itself. So I just removed the screensaver app altogether ```
sudo apt-get remove gnome-screensaver
```I believe.

---

