---
title: "Software updater telling me boot partition is full"
date: 2016-03-14
forum: General Help
---

### Post by clive6 on 2016-03-14
I had an error message saying that my boot sector is full.

 "The upgrade needs a total of 93.8 M free space on disk '/boot'. Please free at least an additional 3,698 k of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I used get clean and also sudo apt-get autoremove but still get the same message. File properties show boot has 90.1 mb free space but I have deleted all the old files

What else can I try?

Best wishes Clive

---

### Post by slickymaster on 2016-03-14
If your computer is running without errors, you should be able to remove old kernels with a simple autoremove command:```
sudo apt-get autoremove
```

---

### Post by clive6 on 2016-03-14
No, I already tried that (see post) AFAIK my computer is running fine, no other error messages

---

### Post by slickymaster on 2016-03-14
First check your kernel version, so you won't delete the in-use kernel image, running:```
uname -r
```Now run this command for a list of installed kernels:```
sudo dpkg --list 'linux-image*'
```Then delete the kernels you don't want/need anymore by running this:```
sudo apt-get remove linux-image-VERSION
```Replace VERSION with the version of the kernel you want to remove.

---

### Post by clive6 on 2016-03-14
Thanks for this. The installed kernel is 4.2.0 - 25 generic

The response to the list of installed kernels was:

dpkg-query: no packages found matching linux-image*
sudo dpkg --list linux-image*


I had removed them all manually

---

### Post by ian-weisser on 2016-03-14
> **clive6 said:**
> I had removed them all manually

Please elaborate. Thatsentence could have many meanings.

Removing kernel packages the wrong way may break your system.
Are you *sure* you didn't remove your running kernel? That would also break your system.

---

### Post by slickymaster on 2016-03-14
> **ian-weisser said:**
> Please elaborate. Thatsentence could have many meanings.

Removing kernel packages the wrong way may break your system.
Are you *sure* you didn't remove your running kernel? That would also break your system.

This ^^^

---

### Post by clive6 on 2016-03-15
I used  [COLOR=#000000][FONT=Ubuntu Mono]uname -r to give me the current image which was- generic and I did not delete that I deleted three or four older images. That said my system would not reboot and I am now using a DVD ROM version of 15.04 to access this forum.... I think I will back up my files and start again lol[/FONT][/COLOR]

---

### Post by clive6 on 2016-03-16
Since I reinstalled, autoremove is working fine. Thanks for your help. Not sure what was wrong but it's fine now!

---

### Post by PJW9779 on 2016-04-02
I run Kubuntu 14.04 64bits and ran into the same problem : disk usage 100% all of a sudden.
But despite thorough searching none of the offered solutions solved my issue.
Until I finally found the easy and quick solution on [http://ubuntuforums.org/showthread.php?t=1830579http://]("http://ubuntuforums.org/showthread.php?t=1830579http://")

_Proceeding as follows :_
1.  I installed Baobab
2.  As root I had Boabab analyze my system
3.  Boabab showed me the largest directories
4.  I then zoomed in by clicking on the pie chart.
5.  In my case /var/log showed to be the culprit
6.  Using Dolphin as root I went to /var/log
7.  /var/log showed a HUGE ufw.log, and also large earlier instances of the same
8.  Using Dolphin as root I deleted all instances of ufw.log
9.  Rebooted
10. TADAA!! My root partition usage is now 14% instead of 99% and my system boots faster and is more responsive

---

### Post by ian-weisser on 2016-04-02
Different problem: /  vs /boot.
Deleting logfiles will not help a full /boot

---

