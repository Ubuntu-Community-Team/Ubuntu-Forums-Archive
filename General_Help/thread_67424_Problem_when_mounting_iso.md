---
title: "Problem when mounting iso"
date: 2005-09-20
forum: General Help
---

### Post by Sonobana on 2005-09-20
Hi!

When i try mount iso with command  sudo mount -t iso9660 -o loop /home/me/image.iso  /home/samuli/oldimage/ i got error message:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And dmesg says:

loop: loaded (max 8 devices)
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.

I have tryed mounting with few iso and i get always same error. So how i fix this problem? I use 2.6.10-5-k7 linux-image. Thanks

---

### Post by KingBahamut on 2005-09-20
[QUOTE=Sonobana]Hi!

When i try mount iso with command  sudo mount -t iso9660 -o loop /home/me/image.iso  /home/samuli/oldimage/ i got error message:

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

And dmesg says:

loop: loaded (max 8 devices)
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.
Unable to identify CD-ROM format.

I have tryed mounting with few iso and i get always same error. So how i fix this problem? I use 2.6.10-5-k7 linux-image. Thanks[/QUOTE]
 That sounds vaguely like a bad ISO. 

Can you verify its integrity?

---

### Post by Sonobana on 2005-09-20
[QUOTE=KingBahamut]That sounds vaguely like a bad ISO. [/QUOTE]

I have tryed mounting with few iso and one mdf and i get always the same message, so i think thats not the problem

---

### Post by KingBahamut on 2005-09-20
mount -t iso9660 /location/of/iso /mountpoint/of/iso/directory -o ro,loop=/dev/loop0

this does what?

---

### Post by Sonobana on 2005-09-20
[QUOTE=KingBahamut]mount -t iso9660 /location/of/iso /mountpoint/of/iso/directory -o ro,loop=/dev/loop0

this does what?[/QUOTE]

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

 ](*,)

---

### Post by X3N on 2005-09-29
After mount -t iso9660 something.iso /mnt/iso/ -o ro,loop=/dev/loop0 not working i looked into the /dev/ and loop0 didn't exist so i changed it to the next logical /dev/loop/ in there which was /dev/loop/0 

mount -t iso9660 something.iso /mnt/iso/ -o ro,loop=/dev/loop/0 

this to works for me

---

