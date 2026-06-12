---
title: "Help! Expensive External HD isn't recognized by Ubuntu, Windows Vista, Windows XP!"
date: 2008-05-16
forum: General Help
---

### Post by Redrazor39 on 2008-05-16
I have a 120 GB HD that I bought a year or so ago (and memory was more expensive, obviously, so I don't want this wasted) and now neither windows xp, vista, nor ubuntu will recognize it! I used it as Windows Live OneCare backup but then formatted it in Vista, but it wasn't recognized. Then, I plugged it in XP AND found out the format wasn't done, so I did a quick format in NTFS. Now none of the computers will recognize it!

Please help!

---

### Post by joshsmith on 2008-05-16
install gparted in ubuntu.
see if it reconizes it (will be shown in top right of window in a drop down menu)
also gives you formatting options

---

### Post by carl99fan on 2008-05-16
I have a similar problem I just purchased a Seagate freeagent pro 320 gig sata hard drive just plugged it in and I get a message.....
cannot mount volume...
little different than your problem mine is because I am so Green at Ubuntu lol

---

### Post by Redrazor39 on 2008-05-16
gparted does not recognize the lacie external HDD either

---

### Post by strabes on 2008-05-16
Please make sure the hard drive is on, plug it in to the computer, run the following commands in a terminal (Applications > Accessories > Terminal), and paste their output here. ```
sudo fdisk -l
ls /media
```

---

### Post by Redrazor39 on 2008-05-16
> **strabes said:**
> Please make sure the hard drive is on, plug it in to the computer, run the following commands in a terminal (Applications > Accessories > Terminal), and paste their output here. ```
sudo fdisk -l
ls /media
```

Done:

sudo fdisk -1:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38c93de4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         833     6682624   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         833       15087   114500440    7  HPFS/NTFS
/dev/sda3           15088       19272    33616012+  83  Linux
/dev/sda4           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

```


and for ls /media

```
cdrom  cdrom0

```

---

### Post by strabes on 2008-05-16
You are right, there is nothing in the fdisk command. How about the output of this command? ```
lsusb
```This problem may be beyond my knowledge, or it may be a problem with your hardware. The fact that it isn't recognized by linux or windows makes me think it's the latter.

---

### Post by hal10000 on 2008-05-17
I assume that your external drive is an usb-drive. So, try the command > lsusb -v and search for a line similar to this one:
> 
bInterfaceClass         8 Mass Storage
bInterfaceSubClass      6 SCSI
bInterfaceProtocol     80 Bulk (Zip)

It may be a long output, so you probably have to scroll up to find it. If there is no line which tells you there is an bInterfaceClass calles "Mass Storage" then your disk is not recognized by the usb-subsystem and maybe it is damaged.
If you have installed th gnome-device-manager you may start it and look for an usb-device which is called "USB mass storage ..." (you can aslo use kde-hal-device-manager).

---

### Post by pbeesley on 2008-05-17
ok I'm having this issue as well with a FreeAgent 120gb, it just sits there and ticks at me (yes I have both USB's plugged in)

fdisk -l:
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1b06d931

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd8ce9ff8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9553    76734441   83  Linux
/dev/sdb2            9554        9964     3301357+   5  Extended
/dev/sdb5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd2cffa9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30514   245103673+   7  HPFS/NTFS

```

ls media
```
cdrom  cdrom0  floppy  floppy0   Jupiter  Saturn
```

---

### Post by Xiong Chiamiov on 2008-05-17
Your case seems to be different, since fdisk shows 3 different hard drives recognized.  Which one are you having a problem with?

---

### Post by louieb on 2008-05-17
At one time I had a Maxtor external drive. It would  work sporadicly  if the USB port on the computer used certain Intel chip sets.  (I found this out from Maxtor. - they no longer sell that model).    

My work around was to install a USB card that used another chip set.  Might try it on another computer.

---

### Post by pbeesley on 2008-05-19
> **Xiong Chiamiov said:**
> Your case seems to be different, since fdisk shows 3 different hard drives recognized.  Which one are you having a problem with?

None of these drives. These are my three internal drives. I WAS (yes past tense :) ) having an issue with a FreeAgent Go External drive. I fixed the problem by firstly plugging the two USB connections (yes it needs two :confused: ) into the back of my case rather than the ones on the front. 

After that I could access the drive but it was read only....sigh....anyway I formatted the drive using.....hang on thinking.........can't remember the codes, I'll dig it out if anyone asks. :) 

Thanks

---

### Post by danwood76 on 2008-05-19
The reason it needs 2 USB is due to power, I would bet that the USB ports on the front of your PC are USB 1.1 or at least not a full USB 2.0 spec.

To the OP:
I think the drive or the drive caddy is dead in your case, I would look at taking it back for a refund if possible or if not try taking the drive out and testing it seperatly, you can buy USB drive caddys for next to nothing on ebay.

---

