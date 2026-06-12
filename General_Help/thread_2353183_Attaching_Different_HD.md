---
title: "Attaching Different HD"
date: 2017-02-19
forum: General Help
---

### Post by Quarkrad on 2017-02-19
I need to attach a different HD into my pc in order to try and recover a deleted file.  In the days of 12.04 and 14.04 when this happened (connecting a different HD into the pc) during the end of the boot process a screen launched (if I remember correctly) asking me to press S (to ignore fstab) and continue with the boot to Desktop.  Now I am on 16.04 I'm presented with a text screen welcoming me to *emergency mode*.  There is an option to enter journalctl -xxxx to see the log files or Ctrl D to continue.  When I enter Ctrl D it just loops and I cannot boot to the Desktop.  Is there something I can do, as per 12.04 and 14.04, to boot to my Desktop if I connect a 'strange' disk into my system that fstab does not like?

---

### Post by yancek on 2017-02-19
Generally the message to press 'S to skip' is shown when you do NOT have a drive attached which has an entry in fstab not the reverse.  How about booting up and then plugging in the external drive, have you tried that?   You should see a new disk icon in the panel or a new uuid under /media/user.

---

### Post by Impavidus on 2017-02-20
I never tried this, but the message 'Press S to skip' might appear too in case you have two hard drives with a duplicate UUID, which may happen if the second drive has a cloned image of the first. But in this case, I wonder, maybe the computer boots from the newly added drive (the one from which a file must be recovered), which may contain a broken Ubuntu system.

Putting the hard drive in an enclosure and attaching it after boot may be easiest. Else, make sure the boot order is correct. And it could help if we knew what is on that drive.

---

### Post by Quarkrad on 2017-02-21
The drive is an internal sata ext3 formatted drive with basic data on it - no OS.  I had a bit of a nightmare last night in this endless loop of booting to emergency mode and Crtl D to continue.  It was happening if if took out one of my existing hard disks or inserting this new HD. Eventually I sorted the problem out by editing fstab but win10 didn't have any problem. (I appreciate win10 does not recognise ext3 but I had to load Photorec on my win10 side to see if I could recovery any lost data on the ext3 drive.  I was hoping to use Photorec on my normal ubuntu side but it just does not like this ext3 drive being attached).  If I have to replace one of my drives it looks like re installing the OS is going to be the quickest way forward.  I never experienced this with <16.04.

---

### Post by RobertoRecordo on 2017-03-22
Exactly My Problem - it had not occurred to me that it was related to removing a drive that has an fstab entry, which is what I am doing (temporarily) while testing a third drive.

This is not marked "solved" so I wonder what the elegant way to get the OS to boot is while in "Emergency Mode" ?

Oh, Success!
As it happens, I had made a copy of /etc/fstab as fstabYYMMDD  when I was editing it for the 2nd drive. It was easy to 
```
cp /etc/fstab /etc/fstab<today>
cp /etc/fstab<backup> /etc/fstab
cat  /etc/fstab
```]
The last line of fstab, which mounted the second HDD, was not included. I used ctl-d to retry...

However, the problem persisted, much to my surprise. I had declared victory too soon!

Apparently fstab was not loaded fresh after th ctl-D, a hard boot (with the truncated fstab file) got me back to the GUI.

Can this be marked Solved?

---

