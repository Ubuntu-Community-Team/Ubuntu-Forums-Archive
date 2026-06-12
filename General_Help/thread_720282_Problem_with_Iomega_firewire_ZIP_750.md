---
title: "Problem with Iomega firewire ZIP 750"
date: 2008-03-10
forum: General Help
---

### Post by Xanrov on 2008-03-10
I have an Iomega Zip 750 connected to the Firewire plug of my PC . Under Ubuntu 7.10, the  ZIP drive is powered, manually ejects OK a disk, reacts with the usual noises when inserting one, but nada on the desktop. It seems (fdisk) that the system recognizes it as sdb (I have only one HD which has various partitions of type sda2, sda6 etc...
I tried various ( surely  wrong ) 'mount' commands without success ( except that they raised a stir from the ZIP drive). As usual the mount man page is  bewildering me.
I have just checked that Iomega doesn't provide drivers for Linux/Unix. 
What must I do ? Thanks in advance for any help

PS The disk I have in the drive is Fat32 formatted. Curiously a  Mac HFS formatted mounts itself all right , showing a small Firewire symbol !

---

### Post by Xanrov on 2008-03-10
After some experimentation my problem seems tied to size of ZIP disks. ZIP750 can read/write 750 MB and 250MB ( also Zip 100 but read only).
Well All 250 MB disks ( Mac or PC formatted) are shown correctly when inserted . Mac HFS+ formatted are also OK. Only PC formatted (FAT32) 750MB disks don't show up. This is a mystery to me. Could some Ubuntu guru give an explanation ?

---

### Post by ibuclaw on 2008-03-10
Hi, I'm not a guru and I don't have a firewire device (or experience with using them with linux), but since no one has helped you yet, I thought I might start (in hope that some will take over). :)

Firstly, I've just been reading about firewire devices on this site here:
[http://wiki.linux1394.org/Introduction]("http://wiki.linux1394.org/Introduction")

Linux supports a wide variety of IEEE 1394 devices, though in my search, I've come across some statements that it's still in a rather experimental/testing stage.

Since your trying to successfully add a storage device, the driver you should be using is the "SBP2" driver. 

so maybe typing:
```
 sudo modprobe sbp2 
```

to see if any errors come up.
and if not, check the `/dev/disk/by-id` folder to see if "ieee-1394" or something along those lines comes up.

If your having troubles reading/writing/executing on the disk, maybe putting a setting in /etc/fstab will help.

```
UUID=6AB0419AB0416E1F /media/ieee1394    ntfs    defaults,umask=007,gid=46 0       1
```
except replace my UUID with your device's one, put in your own folder name to mount it and change ntfs for whatever file format your drive is formatted to.


Anyways, the page is here:
[http://wiki.linux1394.org/sbp2]("http://wiki.linux1394.org/sbp2")

If any of it makes sense to you, perhaps you can figure it out.
And you might want to take a close look at the "Dependencies" section in it... It's rather curious, at least,  none of the commands or programs  exist on my box.

Hope I have shed some light on the situation.

Iain

---

### Post by Xanrov on 2008-03-11
Many Thanks , Tinivole, for your help.  I'll certainly explore the trails you have opened to me.
In fact my Firewire connection does work with all Zip cartridges ( 750, 250 and read-only 100 MB) , the only exception being Fat 32 750MB formatted disk. But those were formatted either under Win 98 or  XP on another PC computer. It remains to be seen If I can freely read and write on those , apparently working cartridges  Mac or Windows formatted (hihgly probable) and if a cartridge , formatted under  Vista on the same new machine where I have Ubuntu, is or not recognised.

Actually it's not such a big problem to me, but I hate not understanding things !

Best regards

---

