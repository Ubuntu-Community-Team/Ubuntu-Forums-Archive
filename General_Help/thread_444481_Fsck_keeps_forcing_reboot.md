---
title: "Fsck keeps forcing reboot"
date: 2007-05-15
forum: General Help
---

### Post by viva_cthulhu on 2007-05-15
First of all, greetings, and thanks in advance for your replies.
I'll try to go through the history of the problem - I apologize in advance if I should get too verbal...
AMD, Feisty Fawn, upgraded from Edgy, on a dual boot system sporting two 120gig fat32 maxtors and an ntfs 80gig Western Digital.
Ubuntu was setup and ran fine for several weeks (read/write ntfs partitions, etc); there was a mild problem with the 2 fat32 partitions though: at reboot, there was a massive slowdown and a long series of clusters - what I later discovered to be fsck complaining about some differences bethween - i think - the FATT and some backup of it.
My linux-savy friend suggested i run fsck and - as for the man - I unmounted the partitions and did. Unfortunately, due to bad typing, fsck started checking the linux partition, being immediately stopped with Ctrl + C.
On next reboot, Fsck stated something to the effect of:
"Last write date on hdb6 *(the linux partition)* is in the future, fixing this
Forcing control"
Once controlled, it automatically reboots, stating it has made modifications on the root partition.
Next reboot, the exact same error appears, and fsck reboots again after checking the linux partition.
The same thing happens when I boot in recovery mode.
Changing the system date makes the "last modification is in the future" message no longer appear, but fsck still forces the check and therefore reboots, to my great stress (i thought this error it kept finding was just a wrong system date, e.g. fsck wrote the changes using some weirdo timezone and then found the timestamp wrong after it "converted" to mine).
Booting in the Kubuntu livecd, i ran fsck (incidentially, it appears to have finally managed to fix the old fat32 problem) and detected the same "last write time in the future" error, fixing which does not make fsck stop its senseless rebooting at next reboot.
Is there some way to fix this without a painful reinstalling and/or force fsck to stop putting its dirty hands in my filesystem at startup? I thought of fixing fstab from the livecd but last time I tried a stunt like that (with xorg) there was no way in hell I could convince linux that I had the permissions to edit a root file...
I apologize for the lenght of the post - i am not used to writing them, usually i just manage to google the answer...
Thanks again!

---

### Post by viva_cthulhu on 2007-05-15
SOLVED!
A matter of editing fstab from the livecd as root - a workaround rather than a fix, but at least I am no longer suicidal :)
Thanks anyway!

---

### Post by Chang An on 2007-05-23
How did you do that if you do mind me asking.

---

### Post by viva_cthulhu on 2007-05-27
I apologize Cheng - I only saw the post now!
I booted with the kubuntu live cd, mounted the hard disk with my linux partiton and edited the /etc/fstab file -roughly:
```
sudo mkdir /media/linux
sudo mount /dev/hdb6 /media/linux #where hdb6 is the partition housing your linux installation
kdesu kate /media/linux/etc/fstab
```
I found the line about my linux partition hard disk, looks like this
```
# Entry for /dev/hdb6 :
UUID=1586c996-af51-4b34-9621-72451ee86c8b / ext3 defaults,errors=remount-ro 0 0
```
I changed the last number to 0. This tells fsck to not check the linux partition at startup, so I suggest you run fsck on your linux drive from the live cd if you are experiencing problems, since it will no longer be ran at startup.
As I said, it's not a fix - it's a workaround! Hope it helps.

---

