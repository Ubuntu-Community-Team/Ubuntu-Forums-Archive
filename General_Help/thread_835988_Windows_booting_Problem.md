---
title: "Windows booting Problem"
date: 2008-06-21
forum: General Help
---

### Post by psycho5 on 2008-06-21
I've been trying so hard to fix my grub after installing windows.

Whenever I restore grub, first mistake it does is that it doesn't label where the OS is located correctly, I always have to edit it. Eg, it should be (hd0,0) for ubuntu but it's always (hd0,1) when I restore grub.

Secondly, I can't boot into windows, I've tried find /boot/grub/stage1 ... root ... setup but all that does is replace my old grub settings, it doesn't actually create a new grub menu does it?

Third, when I just give up hope and try to directly boot Windows by using the super grub cd, It says NTLDR Missing.

So I put in the XP cd and go to the repair console, I copy NTLDR back into C:\ and still no prevail. So I go back into XP setup and this time I do fixboot and fixmbr; I reboot, it loads back the grub menu.

The only time I can actually use xp is after I install it and it boots for the first time, then when I want to go back to linux I have no choice but to restore grub and that messes up my XP boot AGAIN.

My ubuntu is in (hd0,0) which is an IDE 200gb disk.
My XP is in (hd1,0) which is a SATA 320gb disk.

I've read that if it's a SATA drive, it should say (sdx,x) but that's not the case because it does try to boot windows, just gives me the message "NTLDR missing, press alt+ctrl+delete to restart..."

Here is my fdisk -l output:
```

sudo fdisk -l [sudo] password for oj:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c064c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1912 15358108+ 7 HPFS/NTFS
/dev/sda2 7268 38913 254196495 83 Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf475003c

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 6750 54219343+ 83 Linux
/dev/hdb2 6751 7043 2353522+ 5 Extended
/dev/hdb3 7044 8955 15358140 7 HPFS/NTFS
/dev/hdb5 6751 7043 2353491 82 Linux swap / Solaris
```

Current grub menu.lst:

```
## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=fee6d4f8-aa0b-46b4-b594-ec6ec49141e7 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=fee6d4f8-aa0b-46b4-b594-ec6ec49141e7 ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMATIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title ****************************
root

title Non-Linux operating systems:
root

title ****************************
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2 [COLOR="Red"]<---ignore that[/COLOR]
title Windows XP Home
root (hd1,0)
savedefault
makeactive
chainloader +1

```

Is there some other boot loader I can use? Or what can I do? Can I just install XP and configure a DOS boot loader to load Ubuntu? I need alternatives because since 4 days I can't seem to get this to work...

---

### Post by danwood76 on 2008-06-21
The NTLDR missing error is caused because windows isnt on disk 0.
I assume you have it set to boot from your second HD, this is why the drive mapping is strange.

When in ubuntu open up the menu.lst and modify it:
```

sudo gedit /boot/grub/menu.lst

```
Change the Windows lines to be:
```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2 <---ignore that
title Windows XP Home
root (hd1,0)
map (hd0)(hd1)
map (hd1)(hd0)
savedefault
makeactive
chainloader +1

```
This will then virtually map it as HD0 and so windows will like it again.

This is caused because windows likes to be the center of the universe :) (your PC)

---

### Post by VMC on 2008-06-21
> Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c064c

Device Boot Start End Blocks Id System
/dev/sda1 * 1 1912 15358108+ 7 HPFS/NTFS
[COLOR="Red"]/dev/sda2[/COLOR] 7268 38913 254196495 83 Linux

Disk /dev/hdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf475003c

Device Boot Start End Blocks Id System
/dev/hdb1 * 1 6750 54219343+ 83 Linux
/dev/hdb2 6751 7043 2353522+ 5 Extended
[COLOR="Red"]/dev/hdb3[/COLOR] 7044 8955 15358140 7 HPFS/NTFS
/dev/hdb5 6751 7043 2353491 82 Linux swap / Solaris
According to your fdisk, look at red. The Linux is on the 2nd partition, that's why hda(0,1). If you say Windows is on the second hard drive, then it would be hda (1,2)

---

### Post by danwood76 on 2008-06-21
@VMC
If his boot device is set to the IDE disk it will be HD0, so hdb = hd0.
This then makes sense of what he says.

He says the 320GB is his windows (sda0) and 200GB is Ubuntu (hdb0)

---

### Post by VMC on 2008-06-21
> **danwood76 said:**
> @VMC
If his boot device is set to the IDE disk it will be HD0, so hdb = hd0.
This then makes sense of what he says.

He says the 320GB is his windows (sda0) and 200GB is Ubuntu (hdb0)

I see your mapping is correct for Windows, but I didn't see where he told us how the BIOS was setup for the drives.

---

### Post by danwood76 on 2008-06-21
He didnt but I made an educated guess on what he has it set to.
IDE will be the first boot device by default, he also said that hd0,0 works as a boot option to boot ubuntu.

Thus IDE is the root device (hd0) and so my mappings come from that, they should work fine.

---

### Post by psycho5 on 2008-06-21
> **VMC said:**
> According to your fdisk, look at red. The Linux is on the 2nd partition, that's why hda(0,1). If you say Windows is on the second hard drive, then it would be hda (1,2)

Man look at the list again, that ones with the astrisks are my boot disks, the * on the first NTFS is XP and the * on the second one is UBUNTU man


And I tried map (hd0) (hd1) 
            map (hd1) (hd0)

It tries to boot Windows it says Unidentified Device String...

---

### Post by psycho5 on 2008-06-21
> **danwood76 said:**
> He didnt but I made an educated guess on what he has it set to.
IDE will be the first boot device by default, he also said that hd0,0 works as a boot option to boot ubuntu.

Thus IDE is the root device (hd0) and so my mappings come from that, they should work fine.

Bios points to IDE as primary

Wouldn't matter anyway, I can disable the IDE in Bios and grub can still boot my partition if I install it on the SATA. 

That being besides the point, how can I fix this problem?

---

### Post by geo909 on 2008-06-21
Btw there is always "super grub disk".. You can give it a try, it claims that it restores grub automatically.

---

### Post by psycho5 on 2008-06-21
I've been trying to fix this with super grub... I am not an expert with it.

---

### Post by chrisblue on 2008-06-23
I could really do with some help on this topic as well. I reinstalled Hardy on a couple of partitions of my Windows drive as below and probably re installed grub during the install. Previously it was working fine dual booting to either XP or Ubuntu.

Initially I had an Error 15 at stage 1.5 and I followed the instruction

sudo grub
find /boot.grub/stage1
root (hd?,?)
setup (hd0)
quit

After that I could at least see the boot loader screen however each ubuntu menu items give me error 22 - from memory "can't find partition" the windows XP entry give me can't find ntldr and requires a reboot.

My drives are set up as follows
sda and sdb are mirrored data drives
sdc is the operating systems drive
sdd is a non critical data drive

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x688f5bdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14593   117218241   42  SFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x688f5bdc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241   42  SFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40334032

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sdc2            9562       11993    19535040   83  Linux
/dev/sdc3           11994       19288    58597087+  83  Linux
/dev/sdc4           19289       19457     1357492+   5  Extended
/dev/sdc5           19289       19457     1357461   82  Linux swap / Solaris

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x49a28b7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS
```I can't even find a grub-menu.lst file anywhere except the default one do I need to create it.

Any help with this will be much appreciated since I have just reinstalled Ubuntu because I borked my permissions totally and now I seem to have screwed the reinstall to the point where I can't even get into my Windows system :(

---

### Post by danwood76 on 2008-06-23
When you say you cant find your menu.lst I assume you are on the live CD.
Have you mounted your linux partition?

To mount your linux partition do the following i the terminal:
```

sudo mkdir /media/ubutnu # Create the mountpoint
sudo mount -t ext3 /dev/sdc2 /media/ubuntu # Mount sdc2 to the above mountpoint

```
Ubuntu should then appear on your desktop from which you should be able to navigate to your /boot folder and dump your menu.lst to here.

---

### Post by chrisblue on 2008-06-24
OK Thanks found the menu.lst as below

```
## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=61e2cfe7-4353-42eb-90a8-e96a2063c19b ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd2,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=61e2cfe7-4353-42eb-90a8-e96a2063c19b ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd2,1)
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title        Microsoft Windows XP Professional
root        (hd2,0)
savedefault
makeactive
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader    +1
```and this is the output from grub> find /bot/grub/stage1

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd2,1)
```

So hd2,0 is the 3rd hard drive (sdc) and the 1st partition, right? Which should be correct as far as I can see.

---

### Post by danwood76 on 2008-06-24
Do you know which drive you have set it to boot from?

It will be correct if you are booting from the first HD (It only boots the MBR code and not the actual drive) If you have it set to the 3rd drive then this figure should be hd0,1.

You can find out which drive you are booting from in your BIOS setup screen, usually under advanced BIOS features.

---

### Post by psycho5 on 2008-06-24
Hey I managed to fix my boot problem quite easily.

The problem is this solution might not work with everyone since it requires some extra space.

I just created another small partition on my first disk, and installed Kubuntu (or any other linux OS would do) and it installed grub on the first disk.

After installation reboot, my windows was bootable :) even though it was on the 2nd hard drive (SATA)

---

### Post by djpc on 2008-06-24
I have a similar problem apart from when I try to boot to windows it just restarts immidialy. I have tried everything on here but nothing has helped:(

---

### Post by chrisblue on 2008-06-24
Managed to get grub configured right and all OS are booting OK now! phew.

Big thanks to dan for putting me onto the right track and showing me how to mount a drive from the LiveCD.

I found these two sites very helpful for understanding grub and for the windows configuration

[http://www.dedoimedo.com/computers/grub.html#mozTocId29646](http://www.dedoimedo.com/computers/grub.html#mozTocId29646)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu)

and @ djpc. That doesn't sound like a grub problem, if it actually boots into Windows then maybe a virus is the issue??

---

### Post by danwood76 on 2008-06-24
@djpc
Is the windows install on a seperate drive?
And what motherboard do you have?

On my machine back home I was unable to dual boot from grub as my motherboard didnt like it, it would just reset instantly upon selecting windows.
I ended up using GAG to do my dual boot, its very simple to install and setup and it worked perfectly on my system.
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

