---
title: "MS-DOS Disk cloning (using whole disk image)"
date: 2019-12-08
forum: General Help
---

### Post by opsetech on 2019-12-08
I have two 44 pin Flash modules one with 32MB from Transcend and another 256MB from Toshiba (Old industrial ssds)

I want to clone the 32MB one from Trancend with the exact partitioning and the data and write everything into the 256MB one (I don't care about the wasted space)

However I don't know what format does it have or wether it uses MBR or not.

Is there anyway to get an image from whole disk?

---

### Post by The Cog on 2019-12-08
> Is there anyway to get an image from whole disk? 
Yes,assuming that these modules show up as drives.
You need to know the id of the drives, e.g. /dev/sdb or /dev/sdc etc. and just omit the trailing partition number. The command **lsblk** will list all the drives and their sizes - this should be good enough.
**Assuming** the 32M drive is /dev/sdb and the 256M drive is /dev/sdc, then the command would be:
```
sudo dd if=/dev/sdb of=/dev/sdc bs=1M
```
The arguments are input file, output file and block size (default block size is 512 bytes which can be slow).
**Don't get the device names wrong** or you could end up overwriting your system disk!!!
If you prefer, you could make an image file and then use dd a second time to copy the image file to the larger drive. That way you don't have to plug both drives in at the same time, but be careful checking the drive names (sd*) they get given:
```
sudo dd if=/dev/sdb of=imageFileName bs=1M
sudo dd if=imageFileName of=/dev/sdc bs=1M
```

---

### Post by HermanAB on 2019-12-09
Just copy the device.  On UNIX, anything that can copy a file, can also copy a device, there is nothing special about it.  The Data Definition command is popular with some, but you could use the good old kitty cat (or netcat, socat, ftp, head, tail... the list goes on and on).

If both disks are on the same machine then it is very easy, ***but you need to boot off a USB thingy or CDROM, not the disks that you want to copy***:
$ sudo cat /dev/sda > /dev/sdb

You could even  pipe the whole kaboodle through a network connection to another machine using netcat:
On one machine listen with netcat and send its output to a device (it will wait for data to come in):
$ sudo nc -l 1234 > /dev/sda

On the other machine send the device to the other host (which will then write it to the empty disk):
$ sudo nc ip.add.re.ss 1234 < /dev/sda

---

### Post by opsetech on 2019-12-09
Thank you, 

I will try dd command , however, should I do the partitioning myself? 
because the flash modules are bootables therefore I can't simply copy contents as I already tried copy pasting and it didn't work.

---

### Post by SeijiSensei on 2019-12-09
I prefer ddrescue myself. "sudo apt install gddrescue" to install.  (The "g" stands for "[GNU]("https://www.gnu.org/software/ddrescue/").")  I've used it to clone the SATA hard drives in two laptops onto SSDs.  Worked flawlessly both times.

Both ddrescue and the pure dd command do a bit-for-bit copy of the source device on to the target. You don't need to do any partitioning yourself.  These commands treat the source device as a single large binary file and ignore things like partitions.

Both devices need to be unmounted for these commands to work correctly.

---

