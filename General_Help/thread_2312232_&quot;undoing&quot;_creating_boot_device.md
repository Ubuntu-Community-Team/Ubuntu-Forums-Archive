---
title: "&quot;undoing&quot; creating boot device"
date: 2016-02-02
forum: General Help
---

### Post by james-kingdon1 on 2016-02-02
So in the attempt to recover my fiancé’s laptop by installing Ubuntu I accidentally wrote over her SDCard. It got overwritten as a boot device. I did not know it was plugged in or that there was even an SDCard slot. Is there a way I can "undo" the creating boot device, then file recovery to regain the photos and files that were on the drive? I've done similar recoveries off of windows based hard-drives but no longer have that software (not to mention it'd be greatly outdated even if I did). Any help would be greatly appreciated, it apparently had several memorable photos and has no known back-ups that were not lost in the hard-drive crash.

---

### Post by sudodus on 2016-02-03
You have (probably) overwritten part of the data on the SD card. Those data are lost. But the data belonging to many pictures are probably still there and available, at least via ***photorec***, even if you cannot restore the previous partition table and file system.

The data are valuable, so it is a very good idea to ***make a cloned copy*** to a card or pendrive of at least the same size, and try to repair the file system and/or recover files from the cloned copy.

Install ddrescue ```
sudo apt-get install gddresue
``` learn about it at the info page ```
info ddrescue
``` and follow one of the examples.

Learn how to get and how to use ***testdisk*** and ***photorec*** from the instructions at [https://www.cgsecurity.org/](https://www.cgsecurity.org/)

If you need more detailed help, please ask! If I cannot reply, there are many other people who know these methods, and can help you.

See also the following link for more tips: [Howto help USB boot drives](http://ubuntuforums.org/showthread.php?t=2196858)

---

### Post by yancek on 2016-02-03
There really would not be any reason to install Ubuntu to 'recover' the laptop as you can use it as a Live CD with a functional operating system.  Best not to use the installed system any longer because it will continue to overwrite data as long as you do that.   You can download testdisk to the Live CD of Ubuntu and run it from there.

---

### Post by james-kingdon1 on 2016-02-03
Awesome thank you very much I greatly appreciate your help. And especially for thinking of trying the cloned copy.

---

