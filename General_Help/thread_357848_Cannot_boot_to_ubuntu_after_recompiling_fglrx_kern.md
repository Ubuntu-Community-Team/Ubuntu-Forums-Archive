---
title: "Cannot boot to ubuntu after recompiling fglrx kernel modules"
date: 2007-02-10
forum: General Help
---

### Post by rudlavibizon on 2007-02-10
After updating kernel via automatic update (2.6.17-10 to 2.6.17-11) i recompiled the kernel modules (whatever that means :redface:  )  following advice from [this tutorial]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") which means i did this:

```
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
```

Then i rebooted. The booting process starts normally and the splash screen shows up but stops at about 1/3 of the progress line. Please help! :( 

PS. After updating the kernel i rebooted normally but had mesa drivers instead of ati which is why i made this mess

---

### Post by teaker1s on 2007-02-10
so you are saying you have wrong display driver installed?
if yes then at grub, boot recovery and type
[COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR]
change to the correct driver for ati and then 
[COLOR="Red"]sudo reboot[/COLOR]

---

### Post by rudlavibizon on 2007-02-10
Ok, i just tried to boot in single user mode and the same thing happens (probably). Apparently it (the booting process) stops at "checking file systems  fsck 1.39 (29-may-2006) which is after "checking root file system fsck 1.39 (29-may-2006) [ok]" .

What is this got to do with video card drivers, I wonder? :confused:

---

### Post by teaker1s on 2007-02-10
I've had the same problem fsck on edgy has been terrible, feisty I still have issues too.
It's hanging on file system check-sometimes several reboots the fsck will complete

---

### Post by rudlavibizon on 2007-02-10
@ teaker1s: After the kernel update (and a reboot) i had Mesa and I wanted fglrx which is what I had before. So i thought i should do what that tutorial said. I did this before (on the previous kernel update and had no problem.

---

### Post by teaker1s on 2007-02-10
I've only used Nvidia, all I was proposing to do was reconfigure xserver with correct driver, there have been several people which kernel update killed gui and reseting xserver sorted.
I'm sorry I can't suggest more, but I've had no ATI experience

---

### Post by rudlavibizon on 2007-02-10
It's ok now, i rebooted and let it hang and went outside for a walk and when i got back i saw the login screen. fglrx works and all...It seems that it was a false alarm. If i didn't have such a hangover I'd probably freak out. Sometimes having too many drinks is actually good for you ;) . Thanks teaker1s for support. ):P

---

