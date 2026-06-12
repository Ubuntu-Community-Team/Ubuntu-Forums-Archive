---
title: "Ubuntu LiveCD unbootable"
date: 2007-08-05
forum: General Help
---

### Post by ascendant on 2007-08-05
In my very long quest to swap the data between my hdds, one step is resizing the partitions inside the LVM and then the LVM itself.  In order to do this, I need to have some kind of OS running that can resize partitions inside the LVM at the very least.

I have definitely run out of options here looking for something that can boot on my box, and I need you guys' help!

Warning: you are about to be spammed with info about what I've tried, and this will probably filter out a lot of canned responses.  Oh well.
Motherboard [ECS P965T-A]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?CategoryID=1&TypeID=32&DetailID=681&DetailName=Feature&MenuID=1&LanID=9")  Yes, using newest BIOS.  No, BIOS settings don't do jack.
The [CD (DVD) drive]("http://www.newegg.com/Product/Product.asp?Item=N82E16827151133") is an IDE drive with an[ IDE to SATA]("http://www.newegg.com/Product/Product.asp?Item=N82E16812206002") host adapter.  (the drive is IDE, it is plugged into a SATA port on the mobo using the adapter)
There are two HDDs in my comp: 
one 200GB one at 97% capacity holding Windows
one 320GB one at ~7% capacity holsing a 80MB boot partition and the rest is the LVM.  Inside the LVM is are the home and root partitions.

I have openSuSE 10.2 installed on my computer, not Ubuntu., but this forum is by far the best that I've come across for Linux help. The Ubuntu installer and live CD for Edgy and Feisty cannot boot on my computer (they hang), so I cannot install them.
I made a USB key-version of Feisty Live, and it has a kernel panic.
Knoppix hangs during boot.
DSL hangs during boot.
ZenLive CD has some kind of error during boot, I don't remember which one.
Fedora Core 6 hangs too I think, but I know it doesn't work.
Fedora Core 7 hangs unless I tell it to not detect hardware, in which case it doesn't know of any hardware to install to and is useless.
The openSuSE installer can't detect the CD drive it started from, but it can be made to install from alternate sources (I installed it from images on my Windows drive)
The openSuSE Live CD likewise can't detect the CD it booted from (so it can't mount it) and then promptly has a Kernel Panic.  I made a USB key version of it and it (amusingly) also fails to find and mount the CD drive it booted from, possibly because it didn't boot from CD.
For your amusement, I downloaded and compiled (hah, it sounds so easy there LOL) kernel 2.6.22, and it complains about not being able to mount / and has a Panic.  I can't make an initrd for it:```
roar:/boot # mkinitrd ./initrd-2.4.22 kernel-6.4.22.img
/sbin/mkinitrd: line 3046: ./initrd-2.4.22/etc/fstab: No such file or directory
No '/' mountpoint specified in ./initrd-2.4.22/etc/fstab
```
Ultimate Boot CD doesn't seem to have the required tools to look into and resize volumes within LVMs.
BartPE also doesn't seem to be able to, although I haven't used it ever.
Here's the panic code, it's verisimilar between all the OSs that deign to actually print what makes them hang.```
Kernel Panic - not sycing: VFS: Unable to mount root fs on unknown-block(1,0)
```
-sigh-
Neither PartitionMagic or Acronis Disk-something/whatever can resize an LVM, and don't even begin to look inside it to resize the inner file systems. I've seen nothing else that claims to even detect LVM partitions.
Inside openSuSE, I managed to go to runlevel 1, unmount home and shrink it to 13GB with resize2fs.
After reboot, however, nothing had changed.  I went to 1 again and resize2fs complained that it was already 13GB and wouldn't do anything.  Yes, I unmounted home beforehand: I couldn't unmount root (surprise) because it was in use.

I suspect the reason that only openSuSE can boot relies within the initrd.
Is it possible to go within the initrd that I am running now and use its drivers and modules and such within the initrd of the openSuSE Live CD that is converted to Live USB key? 
Or maybe the Ubunutu Live CD one can be made to not look to mount the CD drive that it so horribly fails at, as well as have its initrd modified to work with my hardware?
Can the kernel be replaced? For instance can I simply swap out the kernel on the Live CDs with the kernel openSuSE is using ATM?

For the love of all things good, is there a simpler way to do this???  I've gone almost as far as I can, and it looks like it's just me, you, and the wall.  I turn to you.

note: consider me a Linux noob.  I know Windows well enough though.  Thank you very much, anyone who even replies to note that they have read this ridiculously long post.

---

### Post by ascendant on 2007-08-15
Never mind, y'all.  I couldn't find anything that worked.  Used Acronis Disk Director Suite and PartitionMagic 8.0 (yes, both together) to delete Linux and copy the Windows partition.

[COLOR="Silver"]It's a PITA to get two Windows partitions working together long enough to delete the old one.  The secret lies in hiding partitions from each other.  That means taking the letters away from both and forcing Windows to assign them dynamically at boot time.[/COLOR]

Anyhow, anyone with more than one hard drive that doesn't have them all used in RAID should put the page file on a different drive than your main OS.  Same goes for Linux, so this isn't offtopic.

Mods: lock? delete?

---

