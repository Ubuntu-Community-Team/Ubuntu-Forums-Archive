---
title: "System cant find /home"
date: 2006-12-24
forum: General Help
---

### Post by telovoyagarcar on 2006-12-24
Whats going on now?
Im trying to log in and i receive an error that the /home directory can not be found? i cant login neither with my user account or the root's. it tells me that will have to use the / directory as home, but after i click OK, i get another error and then i get kicked back to the login screen.
The home directory is located in another partition, and it was working fine the last time i used the computer.
And now i am in windows, and i can access both partitions without any problems.. the home and the root partition.
What could be wrong?

This is happening after i shut down the PC from the power button, because half of the attemps, Ubuntu fails to shut down itself, and forces me to press for 5 seconds the power button otherwise, it will never shut down. i dont know if this might be the reason of the problem.

Any ideas?

---

### Post by taurus on 2006-12-24
Sounds like your Linux partitions are corrupted!!!  Which release are you running right?  Boot with the LiveCD, mount the partition where / is, and have a look at your /etc/fstab.  Make sure the entries in there are right...

p.s.  It's never good to shutdown the machine by pushing the power button every single time!

---

### Post by telovoyagarcar on 2006-12-24
the partition might seem to be corrupted by linux but i said not to windows... i can see and browse both partitions from Windows...
here is the fstab content: (it has 2 extra lines to mount my NTFS partitions..

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=d4ba458c-331a-41e0-880b-b5c42aa5e24c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=485acb17-0c8e-4ebc-b989-0b9ee5dda7a3 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#/dev/sda2 /mnt/ntfs ntfs-3g ro,locale=en_US.utf8,uid=1000 0 0

#/dev/sda5 /mnt/ntfs2 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0


/dev/sda5 /mnt/ntfs2 ntfs ro
/dev/sda2 /mnt/ntfs ntfs ro

```

---

### Post by taurus on 2006-12-24
You only have one root partition, /dev/sda6, so if that is corrupted, then /home which resides under is is also corrupted!  Therefore, you need to run the e2fsck to check your /dev/sda6...

From the LiveCD:
```
sudo e2fsck /dev/sda6
```

p.s.  Your two entries for ntfs look a little punky!!!

---

### Post by telovoyagarcar on 2006-12-25
> **taurus said:**
> You only have one root partition, /dev/sda6, so if that is corrupted, then /home which resides under is is also corrupted!  Therefore, you need to run the e2fsck to check your /dev/sda6...


](*,) Im going to say this for the third time....

"/home" and "/" (root) are in two different partitions!!!!!!!!!!

I have only one 320GB Hard Drive in my computer... and it is partitioned the following way:

c: = primary NTFS partition used for my windows installation
e: = primary NTFS partition used for files, documents and stuff in windows/Linux (sda2)
f: = first part of an extended partition for temporary stuff like downloads, etc. NTFS (sda5)
**Root** = Second part of the extended partition that contains the Linux installation **WITHOUT** the /home directory.
/home = Third part of the extended partition that **DOES CONTAIN** the /home directory of linux, and i remember this was sda7 when i did the installation.
swap = the 4th and last piece of the extended partition used as the swap space for linux. This was detected as sda8 during installation
g: = primary NTFS partition and the last one used for a very minimal windows installation used only for games.

so my hard drive is divided in 7 pieces and **3 of them** are for linux = root, home and swap.

So the /home partition (AKA sda7) is not being seen by linux... **BUT** i do can see it with every file in it from windows XP, using a driver that lets me mount, browse and write ext3 partitions within windows...

I hope now you do understand what is going on.

Thanks a lot!

And Merry Christmas!!!!

---

### Post by NeoLithium on 2006-12-25
The sda7 mount point doesn't say /home   Edit the fstab to reflect that; linux can't find it because it's not named, as far as I can see.

---

### Post by telovoyagarcar on 2006-12-25
I GOT IT!!!!

My fuc-----king bad!
I found a backup of fstab that i made before i DID MODIFY IT, when i added the 2 last lines to mount the NTFS partitions.
Somehow, when i did that, the line containing the details about the partition containing the home directory, was accidentaly deleted :p .
I forgot about that backup because i was away from home the last 4 days...
i got it working now..
thanks anyway.

---

