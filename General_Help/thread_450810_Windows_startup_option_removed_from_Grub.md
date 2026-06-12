---
title: "Windows startup option removed from Grub?"
date: 2007-05-21
forum: General Help
---

### Post by NuNn DaDdY on 2007-05-21
Hello, last night when I was done using my computer I simply closed the lid and the computer eventually died running on batteries.  But when I went to start my computer today I noticed that my windows option had been removed and a new ubuntu option was available for choosing.  I went into the menu.list file in grub but there is no longer a windows option available.  I was wondering if anyone knew the code to put in the menu.lst file so I can load up in windows again.  Thanks.

---

### Post by Happy_Man on 2007-05-21
Here, add this to the end:

```
title              Windows
root           (hd0,1)
savedefault
makeactive
chainloader      +1
```

---

### Post by ghell on 2007-05-21
Mine looks like this:```
title Windows
rootnoverify (hd1,0)
makeactive
chainloader +1
```I'm not sure if the rootnoverify or savedefault make a difference. There is probably a template in the comments of your menu.lst```
#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#
```

---

### Post by NuNn DaDdY on 2007-05-22
Thank you for the help, but when I tried both suggestions I restart my machine and then click on the windows icon but recieve a message stating something similiar to "invalid path".  Are there any other suggestions to this issue or is there a way to find out what the root path is?

---

### Post by ghell on 2007-05-22
Have you checked your /boot/grub/device.map to make sure your windows partition is showing up in the correct place?

I don't know if this will work if you have ubuntu and windows on different partitions of the same hard drive, I use separate drives so I have the windows nt loader on the MBR of my SATA RAID and grub on the MBR of my old IDE drive

---

### Post by NuNn DaDdY on 2007-05-22
When i check the device map it only shows up with the following:

      (hd0)	/dev/hdc

---

### Post by fragos on 2007-05-22
Your problem lies in the fact that menu.lst refers to drives differently than Linux in general.  The first hard drive will be called hda by Linux or hd0 by grub.  Linux only really looks at partitions with the first physical partition being called hda1 which be called hd0,0 by grub.  Chances are you started with a Windows OS instalation before installing Ubuntu.  The Windows partition got downsized to make room for Linux and Windows will be at hd0,0.  I believe your problem is just that and Window is at hd0,0.  Edit menue.lst to reflect that change.

---

### Post by ghell on 2007-05-23
How /dev/hd*# correspond to (hd#,#) is not that straightforward.  device.map gives the conversions.

If you have /dev/hdc as your only hard drive and windows and ubuntu are both on this but in different partitions, your device.map is good enough you just need to put the correct partition (hd0,0) (hd0,1) (hd0,2) or whatever in your menu.lst.

If you have multiple hard drives, your device.map is only showing 1 (the one ubuntu us on) and you will need to find where your windows hard drive appears in /dev/hd* or /dev/sd* (or /device/mapper/* if it is RAID, this may require DMRAID to be installed, ubuntu can't see fakeraid on its own) and add it to your device.map.

For example if your windows drive was a sata drive at /dev/sda and your linux drive was an ide drive at /dev/hcd you could have the following device.map:

(hd0) /dev/hdc
(hd1) /dev/sda

If you had ubuntu /boot on the first partition of hdc you would use (hd0,0) in your menu.lst (you do, this is what you are doing now)
If you had windows on the 4th partition of sda you would use (hd1,4) in your menu.lst.

Happy Man's suggestion of using root (hd0,1) would only work if windows was on the 2nd partition of your ubuntu hard drive (for example your partitions in order could be /boot, windows, / ) if this is not the case (and it probably isn't) you will need to use a different partition and/or drive. If your windows drive does not appear in your device.map you will need to add it. If you are using fake raid (for example nvidia or siliconimage raid) you will need to install dmraid and then it will be in /dev/mapper somewhere.

running "sudo fdisk -l" should give a list of your devices.

---

