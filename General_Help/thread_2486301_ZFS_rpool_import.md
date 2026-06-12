---
title: "ZFS rpool import"
date: 2023-04-25
forum: General Help
---

### Post by Ruy Benton on 2023-04-25
Thank you for this great OS - UBUNTU :P

I recover Disks, USB and many other type of data media. 

Recover O.S. Disks- MacOS, FreeBSD, OpenBSD, Amiga, Atari ...
we mount this disks - Data or Main Disk (OS) in our Linux, ex. /recover_disk

If a Friend, Student, Client have a computer (ZFS) and the Motherboard burned, we need recover
the data and put this disk - bpool and rpool in another system - computer

I'm using this computer for ex:
_______________________________________________________________________
Ubuntu 22.04.1 LTS
Linux  5.15.0-52-generic #58-Ubuntu SMP  x86_64
Wayland

zfs-2.1.4-0ubuntu0.1
zfs-kmod-2.1.4-0ubuntu0.1

zsysctl    0.5.9
zsysd    0.5.9
________________________________________________________________________

Problem the two disks (this and the other from the other system):
 rpool in this computer = rpool from other system - NAME

 I              "sudo zpool import  -f     rpool_ID             new_rpool___ID"                                    avoid rpool in this  computer.

The 2º problem   mountpoint=/ is the same in other disk mountpoint=/ 

So my first research:
"sudo zpool import               ..."                           but I can't      "-o mountpoint=/mnt ..."

Please your comments and solutions.

Best Regards,
Ruy

---

### Post by MAFoElffen on 2023-04-26
Try it in this format:
```

sudo zpool import -R /mnt new_rpool___ID

```

---

### Post by Ruy Benton on 2023-04-29
> **MAFoElffen said:**
> Try it in this format:
```

sudo zpool import -R /mnt new_rpool___ID

```

Thank you,

I EDIT my post, please read and comment.

If someone don't follow your advise:

             "sudo zpool import  -f     rpool             new_rpool___ID"

The two rpool mount in /

What mess we create ? [IMG]https://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]




2 - Question:

rpool -> new_rpool___ID
and I changed 
mountpoint=/    ->     /mnt
This disk can't be boot in the original computer.
It's possible change ?


Please,     stickie ... , or on the wiki.                                                                                                                                
I don't see many post and tutorials on this.

Best Regards,
Ruy

---

### Post by MAFoElffen on 2023-04-30
I want to help you. I have a lot of experience with ZFS and issues concerning ZFS and Ubuntu itself.

I apologize in advance, but I am really having a problem understanding what you are saying. Please describe what you have going on, what you are trying to do, and what your goal is.

If there is a challenge where there is a language difference in trying to describe, feel free to use Google translate to help with that.

From what I can figure out after rereading this a few times... Are you trying to replace the rpool from another computer this computer as it's root file system?

---

