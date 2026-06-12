---
title: "Audio CD recognized as blank CD-R in Feisty"
date: 2007-12-22
forum: General Help
---

### Post by Bolorino on 2007-12-22
Hi folks,
I'm getting a problem with audio-cd (music inside) in Feisty: They are recognized as blank cd-r.
Data CDs and non audio DVD work fine after loading ide_generic module and activating DMA.

It is a vaio VGN-AR51J laptop with a combo CD-DVD-BlueRay.

This is the hal info 
18:40:44.873 [I] hald_dbus.c:1248: volume.size -> 477710336
18:40:44.873 [I] hald_dbus.c:1232: volume.disc.type -> unknown
18:40:44.873 [I] hald_dbus.c:1264: volume.disc.has_audio -> False
18:40:44.873 [I] hald_dbus.c:1264: volume.disc.has_data -> False
18:40:44.873 [I] hald_dbus.c:1264: volume.disc.is_blank -> False
volume.disc.is_appendable -> False
18:40:44.873 [I] hald_dbus.c:1264: volume.disc.is_rewritable -> False
18:40:44.873 [I] hald_dbus.c:1264: volume.disc.is_blank -> True
18:40:44.873 [I] hald_dbus.c:1240: volume.block_size -> 0
18:40:44.873 [I] hald_dbus.c:1232: volume.disc.type -> cd_r
18:40:44.873 [I] hald_dbus.c:1248: volume.disc.capacity -> 735051776
18:40:44.873 [I] hald_dbus.c:1232: info.product -> Volume
18:40:44.873 [I] hald_dbus.c:1232: linux.fstab.mountpoint -> /media/cdrom0
18:40:44.873 [I] hald_dbus.c:1232: linux.fstab.options -> user,noauto
18:40:44.874 [I] hald_dbus.c:4710: ************************
18:40:44.874 [I] hald_dbus.c:4711: Client to local_server was disconnected for 812c2b8

8:40:44.874 [I] hald_dbus.c:4752: ********* unregistered 812c2b8
18:40:44.874 [I] hald_dbus.c:4753: ***************************
18:40:44.875 [I] blockdev.c:364: entering; exit_type=0, return_code=0
18:40:44.876 [I] blockdev.c:127: Add callouts completed udi=/org/freedesktop/Hal/devices/volume_empty_cd_r
18:40:44.876 [I] hald.c:103: Added device to GDL; udi=/org/freedesktop/Hal/devices/volume_empty_cd_r
[22492]: 18:40:46.619 [I] addon-storage.c:346: Checking whether device /dev/hda is locked on HAL
[22492]: 18:40:46.620 [I] addon-storage.c:354: ... device /dev/hda is not locked on HAL

I've tried with different types of audio-CD (original and copies) with same results.

Any clue will be appreciated.
Thanks :-)

---

### Post by TidusBlade on 2007-12-22
Maybe it's the way you burnt it? Anyways, it's very unlikely, but you might wanna try installing the package called "ubuntu-restricted-extras" to enable MP3 support, maybe it could work or something...
Good luck :)

---

### Post by Bolorino on 2007-12-22
Thanks for your reply TidusBlade.
The problem is the same with original music CDs, and I have no troubles playin mp3.
Mp3 support and ubuntu-restricted-extras are installed.
Thanks again

---

### Post by TidusBlade on 2007-12-22
Hmmmm, have you tried opening the CD with other programs, such as the CD ripper or K3B or VLC?
Sounds wrong, but could be true, that the system itself cannot read the CD, but the software can...

---

### Post by Bolorino on 2007-12-22
No luck with this approach.
I've tried Sound Juicer and Totem. I will try to dump the audio-CD with dd and see what happens.
Thanks

P.S.
I've tried with another original audio-CD and get no blank-CD-R but "CD-ROM" in desktop. Empty anyway, no play at all.

---

### Post by Bolorino on 2007-12-22
I've tried 
```
dd if=/dev/hda of=music.iso bs=2048 conv=notrunc
```
with an original music CD in the reader and get 
dd reading `/dev/hda': Input/output error

There is no error with data CD.

P.S.
Same error with cat /dev/hda > image.iso
dmesg output:

```
[49566.616000] ide: failed opcode was: unknown
[49566.616000] hda: error code: 0x70  sense_key: 0x05  asc: 0x64  ascq: 0x00
[49566.616000] end_request: I/O error, dev hda, sector 4
[49566.616000] Buffer I/O error on device hda, logical block 1
```

---

### Post by TidusBlade on 2007-12-22
My only guess at this point is that linux cant really read it, so I would usually do it from another computer and then drag the files into Linux, but thats not what your asking for :p 
Maybe try another drive if you have one? Im pretty stumped here...

---

### Post by Bolorino on 2007-12-22
The audio CDs work in another PC with Feisty, so I think the problem is related to the (quite new) CD unit.
I have no external CD unit to try, but maybe can get one.

Thank you TidusBlade :-)

---

### Post by TidusBlade on 2007-12-22
Didnt actually do much :p 
/me gets a brainstorm.
You might wanna try reading them in VirtualBox and then putting them in a shared folder and you can easily use them in linux then?

---

### Post by Bolorino on 2007-12-22
The VirtualBox could be an option.
I will give it a try.
:-)

---

### Post by TidusBlade on 2007-12-22
IT just might take a little time since you gotta installa whole OS...

---

