---
title: "Location of Grub?  (vmplayer boot problem)"
date: 2008-05-03
forum: General Help
---

### Post by Innova on 2008-05-03
I just did a clean install of 8.04.  Previously, in 7.10 I could boot an existing Windows XP installation into vmplayer.

I saved my .vmx and .vmdk files, and after the installation of 8.04 I had to change ide0 to sda0 in the .vmdk file.  After that vmplayer would try to start, but it could not find an operating system to boot to.

I would like to either point it to my windows partition, or even Grub, so that I could boot my windows partition.  Do I have to create a new windows MBR file?  (Previously vmplayer would boot to GRUB and I would have to choose windows).

Here is what parted prints:

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  105GB  105GB   primary  ntfs              
 2      105GB   248GB  143GB   primary  ext3              
 3      248GB   250GB  2147MB  primary  linux-swap       

Under Linux my Windows partition is /dev/hda1.

What am I missing?

---

### Post by DixieWolf on 2008-05-03
so, its listed as /dev/hda1?
for me, mine would be /dev/sda1 as the listing.
did you try hda0 instead of sda0?

I really don't imagine that you would have to rewrite the MBR.
I'm assuming that you went w/ the standard GRUB installation onto the MBR?
If so, and looking at your partitions, as long as you're pointing at the windows partition, and the boot flag is enabled on it, it should work right.

---

### Post by Innova on 2008-05-03
So here is what I have:  

In windows.vmx:

sda0:0.present = "TRUE"
sda0:0.fileName = "windows.vmdk"
sda0:0.mode = "independent-persistent"
sda0:0.deviceType = "rawDisk"
sda0:0.redo = ""
sda0:0.writeThrough = "FALSE"
sda0:0.startConnected = "TRUE"


In windows.vmdk:

# Disk DescriptorFile
version=1
CID=2c039705
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "windowsxp.mbr" 0
RW 488397104 FLAT "/dev/hda" 63  #I've tried /dev/sda, sda0, and sda1 also

# The Disk Data Base
#DDB

ddb.toolsVersion = "0"
ddb.adapterType = "ide"
ddb.virtualHWVersion = "4"
ddb.geometry.sectors = "63"
ddb.geometry.heads = "255"
ddb.geometry.cylinders = "30401"


I should also mention that previously I was running 32-bit ubuntu, but now I am running 64-bit (along with 64-bit vmplayer).

Here is the error I'm getting:

[IMG]http://utopiaprogramming.com/previews/vmplayerError.png[/IMG]

---

