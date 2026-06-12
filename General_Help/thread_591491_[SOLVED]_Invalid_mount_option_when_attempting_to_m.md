---
title: "[SOLVED] Invalid mount option when attempting to mount the volume"
date: 2007-10-25
forum: General Help
---

### Post by faradesla on 2007-10-25
Hello.
I've been searching the forums for about an hour and read anything I could find which seemed like it might help. Because I'm posting now, you can guess how that went.

My problem SEEMS like it ought to be simple enough to fix, but I'm having a hell of a time here. A solution would be nice, as I'm currently locked-out of most of my data.

Here's the situation:
There are two hard drives on this system. I JUST upgraded from Kubuntu Edgy to Ubuntu Gutsy. So I'm still figuring out GNOME. I wanted my secondary drive to automount every time the computer started. After digging around for a second, I got some bad advice to type "OPEN" in the "mount options" dialog for that drive. So I did type "OPEN," and now the damned thing is useless. So, thanks a lot to the halfwit who suggested that.

Is there any way to go back and remove that option, so I can at least reach the disk again? It sure would be nice to actually be able to use my computer, here.

I checked /etc/fstab and didn't see anything interesting, but here it is anyway, in case you doubt me.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=de6bfe4d-7d08-4f0b-9fd9-d94d846c8343 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=28fa6f33-5805-4c48-a029-3ad595f23df1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

The disk in question is ext3 formatted, if I remember right. It's not some silly NTFS problem. I simply typed in the wrong mount option, and now I need to know how to get that option out of there. Thanks a lot for any help you can offer.

---

### Post by Shazaam on 2007-10-25
Post the terminal output of this...
```
sudo fdisk -lu
```

(small L)

---

### Post by faradesla on 2007-10-25
> **Shazaam said:**
> Post the terminal output of this...
```
sudo fdisk -lu
```

(small L)

Hey
Thanks for the quick reply Shazaam. But I managed to fix both my problems almost immediately after I made this post. I came back to delete it, but I'll just post what I did, and let the mods decide if this thread is garbage or not.

I opened the terminal and typed blkid
Used the info for hdb1 (my misbehaving disk) to plug into /etc/fstab
That is, sudo gedit /etc/fstab

Now my fstab has these new lines:
# /dev/hdb1
UUID=5e63f28b-5adf-48a4-9343-8e7015437ed6 /media/hdb1     ext3   defaults 0 2

And rebooted. Now the drive not only works, but automounts, as well. Brilliant! *clink of Guiness glasses goes here*

I thank you for the assist, and apologize for getting a bit ahead of myself by posting when I did before. Hopefully this info will help someone else.

---

### Post by Shazaam on 2007-10-25
Nice! You can mark this thread as solved.

---

