---
title: "I only wanted to be able to backup my hard drive!"
date: 2008-06-02
forum: General Help
---

### Post by DaveH999 on 2008-06-02
A brief story:

I just purchased a Western Digital Passport external hard drive, 250 GB, to back up my laptop.

I wanted (and still want) to be able to do two things:

1.Find a program that allowed me to set up what I wanted backed up, push a button, and let it do the rest.
2.Format the drive so that it could be read by Windows and Ubuntu.  If OS X could read it too, that'd be a great bonus, but it's not a deal-breaker.   (I dual boot Ubuntu 8.04 and Vista, and my work has Macs and PCs)

This process has not gone smoothly.

I tried several backup programs available through Add/Remove programs (Simple Backup Config, Home User Backup, Keep, Grsync), and each either failed or transferred only some of the data.  

When only some data backed up, it usually was due to invalid file names --- so, I figured I should switch the drive formatting.

The drive came formatted as FAT32.  I tried formatting to ext3 using Gparted, but it would remount as read-only, with root as the owner.  Couldn't write to it.  Same thing with ext2.

I read on an archive post to try NTFS.  Gparted wouldn't let me format it that way, so I did it in Vista, which formatted and mounted the drive with no errors.

I went back to Ubuntu, which also mounted the drive and Grsync transferred everything smoothly.  Success...

...but wait!  I log back into Vista, plug in the drive --- and it comes back as corrupted.  As Ubuntu still mounts the drive with no problem, I don't think that's true.

Grr :confused:

Does anybody have any suggestions?  I'm open to pretty much anything.

Thanks in advance!

Dave

---

### Post by logos34 on 2008-06-03
did you run error checking w/repair option on it? Did you properly unmount the drive in vista?
> 
If OS X could read it too, that'd be a great bonus, but it's not a deal-breaker. 

NTFS then
> 
I tried formatting to ext3 using Gparted, but it would remount as read-only, with root as the owner. Couldn't write to it.

Ex: USB drive ext3 partition is mounted at '/media/disk'

try:

[B]sudo chown -R username:username /media/disk 

sudo chmod -R 755 /media/disk[/B]

---

### Post by DaveH999 on 2008-06-03
> did you run error checking w/repair option on it? Did you properly unmount the drive in vista?

[LIST]
[*]I haven't run error checking.  How do I do that?

[*]After formatting the drive in Vista, I directly rebooted into Ubuntu without unmounting it.  I assumed Vista would unmount the drive during log-off if necessary.  The next time I plugged it in running Vista, it was corrupted.  Was that a mistake?
[/LIST]

---

### Post by DaveH999 on 2008-06-03
Update: I tried mounting the HD onto OS X Leopard.  It mounted OK, but was read-only.

Anybody have any other suggestions?

---

### Post by SirPerigrin on 2008-06-03
Are you ejecting the drive from both Vista and Ubuntu prior to shutdown? i had issues on my 320GB MyBook a while back that i found were caused by improper removal. Also i dualboot XP/Ubuntu and i have to concur with using NTFS, as much as i hate the filesystem there arent any alternatives that have read/write support in all 3 OS's

---

### Post by logos34 on 2008-06-03
> **SirPerigrin said:**
> Are you ejecting the drive from both Vista and Ubuntu prior to shutdown?

I was thinking along those lines too. ('unclean shutdown'? there's a correct way to do it in windows, where it gives you a message ~'now safe to unplug mass storage device', etc.)  although the fact that you could use it successfully in linux and only encountered the corruption issue after rebooting to vista is odd.  don't have an answer for it

---

### Post by logos34 on 2008-06-03
> **DaveH999 said:**
> [LIST]
[*]I haven't run error checking.  How do I do that?

right-click on the volume in my computer or go to the disk/storage management control panel (be sure to run with repair option)

---

### Post by DaveH999 on 2008-06-04
> right-click on the volume in my computer or go to the disk/storage management control panel (be sure to run with repair option)

"The disk check could not be performed because Windows cannot access the disk."

Bizarre.  Windows itself formatted the drive as NTFS and now it doesn't even recognize that (says it's a RAW file system).

I'm going to try reformatting and being extra-special careful when ejecting it.  Will check back with the results...

---

### Post by DaveH999 on 2008-06-10
Again!  

Windows says the drive is corrupted.  

OS X says it's read-only.  

Ubuntu reads and writes with no problems.

Anybody other suggestions?  Or am I just destined to have a Linux-only external drive?

DH

---

