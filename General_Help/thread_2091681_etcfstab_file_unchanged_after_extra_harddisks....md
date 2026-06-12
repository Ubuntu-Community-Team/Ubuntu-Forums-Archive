---
title: "/etc/fstab file unchanged after extra harddisks..."
date: 2012-12-05
forum: General Help
---

### Post by then_dude on 2012-12-05
Hello,

A friend of mine came along, his harddisk was crashed, so i hooked it up to my system. tried to restore the data...

after disconnection off the harddisk, my pc would not boot, it was trying to mount certain partitions that i had set in the fstab file....

when i was booted in ubuntu a lot of mounting partitions had been pointed to other places...

So my question: is there a way that no original mounting of partitions or dev/sdXXX is changed and that if you hook up a new harddisk, this gets the next sdX and is mounted at a new point in stead of mounting an existing point and pushing the existing harddisk to a new created mounting point. (hope this is clear enough)

thanks

---

### Post by Rebelli0us on 2012-12-05
You didn't need to edit fstab. Run "sudo blkid" to see where your OS is and what needs to go into fstab, then after fixing fstab run "sudo mount -a" to check for errors.

---

### Post by then_dude on 2012-12-08
thanks Rebelli0us,  i checked out those commands.  but if i run sudo blkid  I still do need to edit the fstab file ? i guess so...  Is there a command that prohibits, even if i add a harddisk that this new harddisk gets any mouting point of the previous ones ? (even if the previous ones are disconnected...)  so i can swap harddisks, but if i put back everything original it seems like nothing has happened,  thanks

---

### Post by Bashing-om on 2012-12-08
then_dude; Hi !
Responding to your original question; A lot depends on how you connected your friend's hard drive to your system. If via usb, should have had no problems relating to fstab; as then the mounting would have been through the directory /media. If you installed the hard drive then the pci bus would have picked it up and ubuntu "might" under some circumstances write to fstab.

The thing now is to make sure fstab is good.
IF You Can Boot into the Operating System:
run:
```
sudo fdisk -l
``` to get the "uuid" assignments and compare the "uuids" with what fstab shows.
It is your system and as such you should be aware of how you have the partitions on your system set up. Soooo --- does fstab reflect only your partitions with the correct "uuids" and any other deliberate additions ?

In the event you have problems making these determinations post the out put of the "blkid" command and the output of: 
```
cat /etc/fstab
```else: can mount the partitions from "live" mode from installCD to get the required info.

[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by then_dude on 2012-12-08
thanks Bashing-om  everything runs fine, i disconnected the friends harddisk, started up,  my harddisk were not mounted automaticly, but ubuntu fired up...   then i edited fstab the way it was, and no problem....  but i don't want it to happen again, not that i'm connecting that much harddisks to my system, but still it's something i would like to know  thanks

---

### Post by Bashing-om on 2012-12-08
Glad ya got it sorted out ! ...Ain't ubuntu wonderful ..caveat -> linux assumes you know what you are doing ! Happily will find and mount anything plugged in [manual: attach device through a mount point and mount from command line] and (if no, will tell you why) fstab for mounting when/how/access as you desire.

Please mark this thread as solved from thread tools above.

[INDENT][INDENT]Happy ubuntu'n <== BDQ

[/INDENT][/INDENT]

---

### Post by mcduck on 2012-12-08
> **then_dude said:**
> Hello,

A friend of mine came along, his harddisk was crashed, so i hooked it up to my system. tried to restore the data...

after disconnection off the harddisk, my pc would not boot, it was trying to mount certain partitions that i had set in the fstab file....

when i was booted in ubuntu a lot of mounting partitions had been pointed to other places...

So my question: is there a way that no original mounting of partitions or dev/sdXXX is changed and that if you hook up a new harddisk, this gets the next sdX and is mounted at a new point in stead of mounting an existing point and pushing the existing harddisk to a new created mounting point. (hope this is clear enough)

thanks
Yes, that's exacly what happens if you simply plug in a drive and let the automatic mounting handle it instead of editing the fstab file.

Al long as your fstab is configured using UUID's t specify partitions, and you don't edit the file yourself, any connected drive should not use the same mount points. Also, connecting drives will never result in any changes in fstab, so the file only changes if you do it yourself.

---

### Post by then_dude on 2012-12-08
thanks,  but i sorted it before i posted this topic. But i would like to know if anybody knows a way to lock the fstab file... i can manually mount the harddisk when i'm in ubuntu  thanks

---

### Post by mcduck on 2012-12-09
> **then_dude said:**
> thanks,  but i sorted it before i posted this topic. But i would like to know if anybody knows a way to lock the fstab file... i can manually mount the harddisk when i'm in ubuntu  thanks

My point was that there is no way to "lock the fstab", there's no need for one as nothing will change the file (unless you do it yourself, by editing the file by hand or by using the Disk Management tool to configure the drive).

---

