---
title: "attempt to read or write out of disk error when boot ubuntu"
date: 2013-05-17
forum: General Help
---

### Post by leafbug on 2013-05-17
I am running ubuntu 13.0.4, my laptop is a thinkpad x230. After my installation of ubuntu, when I boot the machine, I occasionly get the attempt to read or write out of disk error,
which I have to power off the machine several times to get a normal boot, I wonder if there is something wrong about my laptop. I search the forum and find some discussion about
this, but I tried without any progress. My bootinfo is [http://paste.ubuntu.com/5674219/](http://paste.ubuntu.com/5674219/), can anyone help me out. thanks

---

### Post by oldos2er on 2013-05-17
Can you post the output of ```
df -h
``` ?

There are some suggestions on freeing up disk space [here]("http://ubuntuforums.org/showthread.php?t=1122670").

---

### Post by linuxtechguy on 2013-05-17
He already posted that on his pastebin. Something else must be wrong.

---

### Post by oldos2er on 2013-05-17
So it is! Thanks.

leafbug, try fsck'ing your disks: ```
sudo touch /forcefsck
``` then reboot. If any errors come up, please let us know.

---

### Post by leafbug on 2013-05-18
thanks for your help, I try your advice, but without success, I enable fsck with the disk, the disk check passed, but it still occurs occasionly.

---

### Post by oldos2er on 2013-05-19
The next thing I would do is to run a smartctl check: [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by leafbug on 2013-05-20
thanks, I will try the smartmontools, hope to get some clue.

---

### Post by leafbug on 2013-06-11
I tried smartctl and found no answer, the problem still occurs occasionally... Is there incompatibility between disk and bios?

---

