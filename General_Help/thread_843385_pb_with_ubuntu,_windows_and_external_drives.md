---
title: "pb with ubuntu, windows and external drives"
date: 2008-06-28
forum: General Help
---

### Post by clotilde83 on 2008-06-28
Hello, 

I am writing a new thread because I tried everything I saw on the different forum and nothing worked. And I don't know what to do anymore. I have to say that I am new with ubuntu and not very good with commands for now.

I have a Dell Inspiron 6000 who was working well.
 Last week, I asked a friend of mine to do a partition and put ubuntu on my laptop. The thing is that now I cannot boot my computer on windows anymore, I tried some commands to access my windows files by ubuntu but it doesn't work either. And my friend doesn't know what to do.

I also have another problem, my computer doesn't recognize my external drives for two days now. And when I try to upload the updates I was the following message, 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
when I put the command as asked, in the terminal it says command not found.

My last problem is that I don't have any sound anymore, but my priorities are the first two problems.



I really hope that someone is going to be able to help me with my problems.



Clotilde

---

### Post by danwood76 on 2008-06-28
For the first problem we need to see the output of a couple of commands.

Open up the terminal and run the following two commands:
```

sudo fdisk -l
cat /boot/grub/menu.lst

```

For the second issue you need to run the dpkg configure command as stated, in the terminal run the following:
```

sudo dpkg --configure -a

```
(These commands can be copy and pasted in)

Sound is sometimes a little tricky, it would help if we knew some more info about your PC.
The following command will dump details of all the components of your PC, post the output here as well.
Its useful when you post these outputs using the code braces (select the text and press the #)

---

### Post by clotilde83 on 2008-06-28
ok, thank you, I put the first command and that is what I get, then I put the second command car /boot/grub/menu.lst, it's say car: command not found.
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+   6  FAT16
/dev/sda2   *           9        3272    26218080    7  HPFS/NTFS
/dev/sda3            6690        7295     4867695   db  CP/M / CTOS / ...
/dev/sda4            3273        6689    27447052+   5  Extended
/dev/sda5            3273        3338      530113+  82  Linux swap / Solaris
/dev/sda6            3339        6689    26916876   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 8086 MB, 8086618112 bytes
249 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15438 * 512 = 7904256 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?       50404      124346   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(50403, 232, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(124345, 119, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdc2   ?       10927      136334   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(10926, 224, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(136333, 143, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdc3   ?      121123      246529   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(121122, 0, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(246528, 167, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdc4   ?      186921      186925       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(186920, 164, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(186924, 63, 33)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

---

### Post by clotilde83 on 2008-06-28
for the second problem (updates) , I forgot to copy what the terminal was saying, but it's working now, thanks !!

---

### Post by danwood76 on 2008-06-28
Sorry that command should have been cat, so:
```

cat /boot/grub/menu.lst

```

Do you have a USB disk plugged in at the moment? (8GB)
It looks like it has a messed up partition table maybe that is why its not mounting?

---

### Post by clotilde83 on 2008-06-28
yes , I had a usb of 8gb I unplugged it.
so, I did the command and the result is 
default 7
timeout 10

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=01b69d1f-3b89-40e4-adcd-40a78f34f22e ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=01b69d1f-3b89-40e4-adcd-40a78f34f22e ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=01b69d1f-3b89-40e4-adcd-40a78f34f22e ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=01b69d1f-3b89-40e4-adcd-40a78f34f22e ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

title Other operating systems:
root 

title Dell Utility Partition
root (hd0,0)
chainloader +1
savedefault

title Windows XP Media Center Edition
root (hd0,1)
chainloader +1
savedefault
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=01b69d1f-3b89-40e4-adcd-40a78f34f22e ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

---

### Post by clotilde83 on 2008-06-28
And the sound is working now too !!!!

---

### Post by danwood76 on 2008-06-28
Well the menu.lst file looks like its configured correctly.

When you select 'Windows XP Media Center Edition' from the grub menu are any errors displayed on the screen?

---

### Post by clotilde83 on 2008-06-28
Hi, 

When I try to start the computer with windows as the operating system, it's says, 

starting up....
grub loading stage 2

and then it goes back to the window where I have to choose between ubuntu and windows to start the computer

---

### Post by danwood76 on 2008-06-29
If it goes instantly back then it sounds like you're chainloading the /boot partition which you are not. (or shoulnt be)

Normally grub halts on errors and gives you a number, its odd as it looks like its configured correctly.
What we could do is try reinstalling the windows MBR and see if windows then boots, it may be that youve installed grub on the boot sector of the widnows partition which will give you issues.

To reinstall the windows MBR do as follows, in the terminal enter these:
```

sudo apt-get install ms-sys
sudo ms-sys -m /dev/sda

```
Upon a reboot windows should then load, if it doesnt than you may have broken your windows install, this can normally be fixed with a windows install CD if you have one.

After doing this if windows doesnt load you will want to reinstall grub to get back to a working system, this can be done from the ubuntu live CD following these instructions:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by clotilde83 on 2008-06-29
I tried but after the first command I have a message error, 
E: Couldn't find package ms-sys

---

### Post by danwood76 on 2008-06-29
Sorry I just had a quick search around and it seems microsoft got that package removed from debian as it has some copyright code in it.

There is an alternative though which should work just the same, here are the updated instructions:
```

sudo apt-get install mbr
sudo install-mbr -i n -p D -t 0 /dev/sda

```
This will install an MBR which will boot the partition with the bootable flag, in your case the windows partition.

---

### Post by clotilde83 on 2008-06-29
ok, I did it and this time, I don't have any error message. But I tried to restart windows and it's still doesn't work. 
So like you said before I have to try to reinstall the grub with the link you gave me.

---

### Post by danwood76 on 2008-06-29
So it still loads grub upon boot up?

Do you have a windows install CD?
It might be worth sticking in the XP install disk and running 'fixboot' and 'fixmbr' from the recovery console.
I have a feeling you have somehow overwritten the boot sector on your windows partition.

---

