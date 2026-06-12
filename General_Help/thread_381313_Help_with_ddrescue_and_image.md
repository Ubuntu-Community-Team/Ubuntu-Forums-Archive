---
title: "Help with ddrescue and image"
date: 2007-03-10
forum: General Help
---

### Post by PiZZLE on 2007-03-10
so i had to recover a bad drive, of a possible 114 gigs it recovered almost all with the exception of 7mb. well, now there is a 114gb .img file in linux that i also have copied to a ntfs drive so i have access to it in vista. but for the life of me i cant mount the .img file in either ubuntu or vista, i have tried EVERYTHING, winrar, magiciso, daemon tools in vista and the loop trick in ubuntu. can someone please help, its 114 gigs worth of mp3's i just want them =(

edit: to give some more info that might be helpful, the image is called "rescue.img" and its located in /media/linux_backup/rescue.img and its about 114GB, i tried doing this command

sudo mount -t iso9660 -o loop /media/linux_backup/rescue.img /mnt/rescue

but it gives me this error

mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

so this is the message i get from dmesg | tail

[17179616.380000] eth0: no IPv6 routers present
[17179617.668000] usb 2-2.2: USB disconnect, address 7
[17179617.800000] usb 2-2.3: USB disconnect, address 9
[17184555.396000] loop: loaded (max 8 devices)
[17184555.508000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17184555.540000] NTFS volume version 3.1.
[17184865.856000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17184865.856000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17184865.856000] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[17185252.028000] Unable to identify CD-ROM format.


update: when trying to replace iso9660 with ntfs when mounting i get this error when trying to access /mnt/rescue

You do not have the permissions necessary to view the contents of "rescue"

new update: i tried to do a "sudo ls /mnt/rescue" it actually lists my directories

so i tried to do a "sudo cp /mnt/rescue/folder /media/new (which is a ntfs drive with ntfs-3g) and i get this error
cp: cannot stat `/mnt/rescue/gaming.music': Input/output error

---

### Post by PiZZLE on 2007-03-11
just wanted to give it a little bump. i can see inside the mounted drive with sudo and list the files, but cant copy them over. please help!

---

