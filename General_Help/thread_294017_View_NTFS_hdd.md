---
title: "View NTFS hdd"
date: 2006-11-06
forum: General Help
---

### Post by Wafflesomd on 2006-11-06
Hello.


I have seen various guides on nfts, but I'm haveing a hard time understanding them, or if they even partain to my issue.

I have a 200gig Maxtor full of music and movies.

Its formatted in nfts, Ubuntu doesnt seem to like that :(

Is there anyway I can read/write ntfs in ubuntu?

Sry if this is stated in one of the guides.

---

### Post by ape on 2006-11-06
When you say "Ubuntu doesn't seem to like that", what error messages are you getting?  Linux has had support for reading NTFS partitions for quite a while now and the writing to NTFS partitions is finally starting to become stable.

Try following the information presented on this link:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")

---

### Post by givré on 2006-11-06
> **ape said:**
> When you say "Ubuntu doesn't seem to like that", what error messages are you getting?  Linux has had support for reading NTFS partitions for quite a while now and the writing to NTFS partitions is finally starting to become stable.

Try following the information presented on this link:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access")
Ok, you should now that the link you mention refer to some old installations instructions  (from dapper, or even breezy).
Until this is fix, if you want up to date writing support fror ntfs, i advice you to go there :

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by Wafflesomd on 2006-11-06
Here is the error I am receving.

error: device /dev/hda1 is not removable

error: could not execute pmount

---

### Post by taurus on 2006-11-06
If you want to read/write to your NTFS, then you need ntfs-3g.  Do a search here and you will find a few posts regarding that subject...

---

### Post by Wafflesomd on 2006-11-06
Ok, I did everything in the tutorial, but i get this:

mount: only root can mount /dev/hda1 on /media/hda1

---

### Post by taurus on 2006-11-06
Put the sudo in front of mount!!!

```
sudo mount .............
```

---

### Post by Wafflesomd on 2006-11-06
I'm sry, I dont follow.

What esacly comes after the "sudo" you told me to put in :(

---

### Post by taurus on 2006-11-06
> **Wafflesomd said:**
> Ok, I did everything in the tutorial, but i get this:

mount: only root can mount /dev/hda1 on /media/hda1
What command did you use to get this error message?  Whatever it is, add a sudo in front of it to mount since only root can mount.  That's what I was trying to say...

---

### Post by Wafflesomd on 2006-11-06
All I did was click the hdd icon to get that message.

---

