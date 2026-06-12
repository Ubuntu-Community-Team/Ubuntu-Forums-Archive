---
title: "Check to see if PSP is plugged in?"
date: 2008-03-21
forum: General Help
---

### Post by Gerlads Mod on 2008-03-21
For those who know PSP stuff, I am trying to make a Pandora Battery installer for Linux.
The guide I am following is here: [http://forums.qj.net/f-psp-pandora-discussion-207/t-guide-creating-a-pandora-on-vista-linux-126194.html#post1856236](http://forums.qj.net/f-psp-pandora-discussion-207/t-guide-creating-a-pandora-on-vista-linux-126194.html#post1856236)

Is there a way I can check with a command if my PSP is plugged in or not?
Also, in the guide it requires you to check **dmesg** to see the name of the file in /dev.
Ex. When you type in **dmesg** in terminal, and you just plugged in the PSP, it should output something like this at the bottom: 
```

[ 9299.909133] sd 9:0:0:0: Attached scsi removable disk sdf
[ 9299.909182] sd 9:0:0:0: Attached scsi generic sg5 type 0

```
And you will have to use sdf and sdf1 for the rest of the process.

So is there anyway to tell if a PSP is plugged in with a command, and is there a way to get the 2 files from /dev without manually searching **dmesg** with a command.


Thanks a ton.

---

### Post by InvIsiBlekID on 2008-03-21
If you type:
```
sudo fdisk -l
```
It'll tell you available partitions (your psp should be listed there).
Good luck with this, I've done a pandora batter before, but from a windows machine.

---

### Post by Gerlads Mod on 2008-03-21
Thanks man that helped a lot.

---

### Post by Gerlads Mod on 2008-03-22
I wonder if there would be a command that could check to see if it's plugged in already. So if it's not it could say "Please plug in your PSP". I know they have one of these for Windows.

Also, when I make Pandora Battery's, you need 1 - 3 EBOOTS. Which are like 20mg's apiece. Would it be better to download these from the web and copy them through a tarball or just directly include them with the download of the installer.

---

