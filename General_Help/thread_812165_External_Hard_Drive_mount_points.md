---
title: "External Hard Drive mount points"
date: 2008-05-29
forum: General Help
---

### Post by daz4126 on 2008-05-29
I've just got a usb external hard drive that is split into 3 partitions - backup, data and music.
These get auto-mounted when I switch the computer on (with the hdd plugged in from boot up).

I've got some strange behaviour going on in the /media folder though:
There are more folders than I would expect:
DATA, DATA_, BACKUP, BACKUP_, BACKUP_, MUSIC and MUSIC_

I'm not sure what these folders with the underscore on the end are, but these are the ones that have the files in (the other folders are empty). The folder access permissions of these folders also keeps changing to be root and I have to open the properties dialouge as root and change it back in order to make any changes.

Has anybody got any ideas what is going on here and what, if anything, I should do about it?

thanks in advance,

DAZ

---

### Post by daz4126 on 2008-05-30
Okay, I've figured out where the weird _DATA folders were coming from - they were left over from when I used a different USB port to plug the hdd into.

I've still got permission problems - 2 of the partitions are listed as being owned by root, so won't let me open them unless I use sudo. Even if I open Nautilus as root and then go to the permissions tab, it won't let me change me ('daz') to be the owner of these files.

Does anybody know how I could change the ownership permissions on these partitions?

Thanks,

DAZ

---

### Post by daz4126 on 2008-05-30
Just to add that the 2 partitions that won't let me change the permissions are formatted as FAT32 whereas the one I can change is formatted as EXT3, I'm not sure if that makes any difference?

DAZ

---

### Post by daz4126 on 2008-05-30
googling around I have found that you can't change the permissions of a FAT32 partition. Most solutions mention editing fstab so that the drive is mounted with the correct permission, but as this is an external USB drive it is not listed in fstab. Any ideas anybody?

cheers,

DAZ

---

### Post by chrisccoulson on 2008-05-30
When you plug in an external drive, it will be mounted with 'root:plugdev' ownership. You shouldn't need to play around with ownership at all. Are you a member of the plugdev group? What is the output of:
```
groups
```

---

### Post by daz4126 on 2008-05-30
Thanks for the reply chris.

This is the output of groups
```

daz adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

```

I see that plugdev is there, how do I find out if I am a member of it?

Funny thing is that I unplugged the hdd and then plugged it back in and I could acces them. Maybe there was a slight hiccup when I plugged in earlier?

cheers,

DAZ

---

### Post by chrisccoulson on 2008-05-30
> **daz4126 said:**
> Thanks for the reply chris.

This is the output of groups
```

daz adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin

```

I see that plugdev is there, how do I find out if I am a member of it?

Funny thing is that I unplugged the hdd and then plugged it back in and I could acces them. Maybe there was a slight hiccup when I plugged in earlier?

cheers,

DAZ

That output means you're already a member of plugdev. I can't explain why it didn't work the first time round though. Very odd!

---

### Post by daz4126 on 2008-05-30
Well, not to worry, maybe I was logged in as root when I plugged it in or something. Thanks a lot for taking the time to help.

DAZ

---

