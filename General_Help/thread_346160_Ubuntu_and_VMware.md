---
title: "Ubuntu and VMware"
date: 2007-01-25
forum: General Help
---

### Post by pod25 on 2007-01-25
Just installed vmware onto my ubuntu 6.10
My problem is, how do I get vmware to use a windows installation thats already installed ?
My laptop was a duel boot, for good reasons, My printer (Lexmark) don't support Linux, it's almost brand new and I refuse to sell at a loss and replace with a printer that will work with Linux.
I'm fed up with having to reboot into windows, so I installed vmware, but i want to use the current installation rather than install a fresh copy.

---

### Post by AlanRogers on 2007-01-25
Dual-boot and virtual machine are not interchangeable but mutually exclusive. If you set up a virtual machine, the files sit within the booted environment, not alongside as in dual-boot. I don't think, but stand ready to be corrected, that you can do what you're looking to do, Linux or otherwise.

---

### Post by taylonr on 2007-01-25
I agree with the previous poster in that you can get the VM to take your windows drive and run with  it. 

However, you can install the printer on your VM.  I have done this for a scanning program that I use in windows, but doesn't work in wine.

You should be able to access all your windows stuff from your VM though.  Here's my set up:
I have HDA with XP on it.
HDB with Ubuntu on it.
HDB has mapped HDA to /media/windows
HDB has samba installed for my other computers
When I launch my VM it is actually running on HDB.
I can go into the Network Folders in my VM and see my Ubuntu desktop.
From there, I can access my Ubunut's /media/windows 

That is how I run the programs I need.

Hopefully that didn't cloud things up any more than they already were.

---

### Post by tszanon on 2007-01-25
Let's see...it's possible to use a whole partition as a disk in a virtual machine. Then you can install the OS in that partition and possibly you can even use that OS outside the virtual machine.

Then, if you create a virtual machine, set the Windows partition as the Virtual Machine HD, probably you can run the existing Windows inside vmware.

Remember: backup your files before attempting anything that may destroy your data.

Probably everything will be just fine, and you'll just have to install vmware's video and mouse drivers. I suppose you may have some driver conflicts, but I'm not sure, because I never tried doing this.

Good luck!

---

### Post by compiledkernel on 2007-01-25
I dont believe its possible to use an existing parition to "create" a virtual machine in VMware. Unless you take a image of the existing partition with Partition magic (or something related in nature) and then boot that onto the existing VMware created image (but even then you might run into issues with hardware being recognized, Im not very sure).

---

### Post by taylonr on 2007-01-25
Perhaps I stand corrected.

This guy ([http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)) apparently got his already "fine-tuned" windows partition to run in a VM.

---

### Post by OnceYouGobuntu on 2007-01-25
I think [VMWare Converter]("http://www.vmware.com/products/beta/converter/") solves your problem. You can use it to convert your windows installation to a VM. It is currently in beta and available for download. I tried it with a WinXP installation - runs slow but worked great. This is a very nice product.

---

### Post by AlanRogers on 2007-01-25
> **OnceYouGobuntu said:**
> I think [VMWare Converter]("http://www.vmware.com/products/beta/converter/") solves your problem... This is a very nice product.It looks like I am corrected; I'll get my coat :^o #-o

---

### Post by pod25 on 2007-01-26
> **taylonr said:**
> Perhaps I stand corrected.

This guy ([http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm)) apparently got his already "fine-tuned" windows partition to run in a VM.

Great link, I'm almost there now, but it's failing on a permissions error when I try to fire up the VM. It doesn't specify where or what the permission errors are, so I'm kinda stuck.

And to the rest who replied, well thanks. I think this could be useful if I manage to get it to work, could save a lot of people a few headaches having to start a fresh with a XP install.

---

### Post by pod25 on 2007-01-26
This is the error I get when I try to power up the VM :
```
Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP Home Edition/WindowsXP.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file.
```

These are the contents of the WindowsXP.vmdk file :
```
# Disk DescriptorFile
version=1
CID=9428f535
parentCID=ffffffff
createType="fullDevice"

# Extent description
RW 63 FLAT "WindowsXP.mbr" 0
RW 156301424 FLAT "/dev/hda" 63

# The Disk Data Base
#DDB

ddb.virtualHWVersion = "4"
ddb.geometry.cylinders = "9729"
ddb.geometry.heads = "255"
ddb.geometry.sectors = "63"
ddb.adapterType = "ide"
```

Any ideas ?

---

### Post by mbeierl on 2007-01-26
Please post the output of ls -al for all the files in that directory...

---

### Post by pod25 on 2007-01-26
> **mbeierl said:**
> Please post the output of ls -al for all the files in that directory...

```
drwxr-xr-x 2 john john  4096 2007-01-26 16:48 .
drwxrwxrwx 3 root root  4096 2007-01-26 17:13 ..
-rw------- 1 john john  8664 2007-01-24 21:01 nvram
-rw-r--r-- 1 john john 20000 2007-01-26 13:34 vmware-0.log
-rw-r--r-- 1 john john 20000 2007-01-26 13:27 vmware-1.log
-rw-r--r-- 1 john john 19999 2007-01-26 11:11 vmware-2.log
-rw-r--r-- 1 john john 20000 2007-01-26 13:41 vmware.log
-rw-r--r-- 1 john john  1394 2007-01-25 21:11 Windows XP Home Edition.vmx~
-rw-r--r-- 1 john john 32256 2007-01-26 13:27 WindowsXP.mbr
-rwxrwxrwx 1 john john   342 2007-01-26 16:48 WindowsXP.vmdk
-rw-rw-rw- 1 john john   340 2007-01-26 13:40 WindowsXP.vmdk~
-rw------- 1 john john     0 2007-01-25 22:08 WindowsXP.vmsd
-rwxrwxrwx 1 john john  1673 2007-01-25 22:29 WindowsXP.vmx
-rw-r--r-- 1 john john  1598 2007-01-25 21:39 WindowsXP.vmx~

```

---

### Post by mbeierl on 2007-01-26
Oh - sorry I didn't read the vmdk contents carefully enough.  I'm not very familiar with the converter stuff, but in your vmdk it's saying that it is going to use /dev/hda as a raw disk.  If that's the case, then you'll need the appropriate permissions on /dev/hda.

This typically involves adding yourself to the 'disk' group and then logging out/back in again.

If not, please post the output of 'ls -al /dev/hda' and the 'groups' command.

---

### Post by pod25 on 2007-01-26
> **mbeierl said:**
> Oh - sorry I didn't read the vmdk contents carefully enough.  I'm not very familiar with the converter stuff, but in your vmdk it's saying that it is going to use /dev/hda as a raw disk.  If that's the case, then you'll need the appropriate permissions on /dev/hda.

This typically involves adding yourself to the 'disk' group and then logging out/back in again.

If not, please post the output of 'ls -al /dev/hda' and the 'groups' command.

john@podmedia:/$ sudo ls -al /dev/hda
brw-rw---- 1 root disk 3, 0 2007-01-26 13:26 /dev/hda

---

### Post by pod25 on 2007-01-27
Bump

---

### Post by pod25 on 2007-01-27
I'm guessing I need to add myself to the group that owns  /dev/hda2 but how do I do that ?

---

### Post by tszanon on 2007-01-29
The easiest way to get by this is giving permissions to anyone on /dev/hda
```
sudo chmod 777 /dev/hda
```

I don't know if it's dangerous or anything, but it solved my problem when I tried to use /dev/sdc as the Virtual Machine disk.
Until you know the risks of doing this, I recommend you to put permissions back after shutting the virtual machine down:
```
sudo chmod 660 /dev/hda
```

---

### Post by bryanpaluch on 2007-02-10
I've been using that tutorial for booting an existing partition. To get pass that permission problem I used a sudo vmplayer from the console to run. My problem is that after selecting the windows.vmx, grub pops up in the vmplayer. After i go down to select my windows partition I am then told to select my hardware profile. After I do this it boots back into grub. I'm guessing it is breaking at some point there. I'm pretty sure i've followed the tutorial to a t. Anyone have any guesses how to get pass that part?

---

### Post by Guajiro_NJ on 2007-02-22
> **bryanpaluch said:**
> I've been using that tutorial for booting an existing partition. To get pass that permission problem I used a sudo vmplayer from the console to run. My problem is that after selecting the windows.vmx, grub pops up in the vmplayer. After i go down to select my windows partition I am then told to select my hardware profile. After I do this it boots back into grub. I'm guessing it is breaking at some point there. I'm pretty sure i've followed the tutorial to a t. Anyone have any guesses how to get pass that part?

Similar issue here. Only, I get passed the GRUB menu, and see the Windows XP splash disk for about 1 second before the XP gives me the blue screen of death.

Anyone see this before?

---

### Post by gabng on 2007-02-22
> **Guajiro_NJ said:**
> Similar issue here. Only, I get passed the GRUB menu, and see the Windows XP splash disk for about 1 second before the XP gives me the blue screen of death.

Anyone see this before?

I'm having the exact problem, would certainly need some guidance.

---

