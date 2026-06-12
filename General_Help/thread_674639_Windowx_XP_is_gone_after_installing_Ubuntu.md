---
title: "Windowx XP is gone after installing Ubuntu"
date: 2008-01-21
forum: General Help
---

### Post by DanielGJ5131 on 2008-01-21
Okay well, I did a big mistake I guess. I installed Ubuntu after having Windows XP installed in my computer. Now when I start the computer, it goes directly to Ubuntu, not letting me choose Windows XP. I'm not sure whether Windows XP is still there, I didn't know what to do once this happened and my computer is one of those laptop that have the reboot files in the D: drive and by pressing F8 during boot will bring up the system recovery screen, I tried this and it didn't work. Now I don't know how to go back to Windows, I cant seem to find a way. I tried researching and I found some commands through the terminal and now I can see XP on my selection list for Operating Systems, but when I choose it, it says invalid operative system. So what I'm left with is, installing Windows XP again from my friends CD or taking the computer to a technician if I cant find a way to go back to windows, since I cant make the factory recovery setup, so could anyone please help me?

---

### Post by DapperMe17 on 2008-01-21
If you chose to let Ubuntu "use the entire disk" when partitioning (during the Ubuntu installation process), your previous Windows would no longer be recoverable. This is, because you reformatted over the entire disk.

If you chose to "manually" partition the disk during the installation process, you'll have to send over furthur detail...

---

### Post by brennydoogles on 2008-01-21
> **DanielGJ5131 said:**
> Okay well, I did a big mistake I guess. I installed Ubuntu after having Windows XP installed in my computer. Now when I start the computer, it goes directly to Ubuntu, not letting me choose Windows XP. I'm not sure whether Windows XP is still there, I didn't know what to do once this happened and my computer is one of those laptop that have the reboot files in the D: drive and by pressing F8 during boot will bring up the system recovery screen, I tried this and it didn't work. Now I don't know how to go back to Windows, I cant seem to find a way. I tried researching and I found some commands through the terminal and now I can see XP on my selection list for Operating Systems, but when I choose it, it says invalid operative system. So what I'm left with is, installing Windows XP again from my friends CD or taking the computer to a technician if I cant find a way to go back to windows, since I cant make the factory recovery setup, so could anyone please help me?

Did you ever have a chance to make recovery cd's in Windows?? If so, just toss one in the drive and reboot, and you should be well on your way!

---

### Post by DanielGJ5131 on 2008-01-21
Oh, I guess I did overwrite my files.. anyway, I cant even run the recovery system so what I'm left with is installing Windows back again, right? Otherwise, what options do I have?

Oh, and Brenny, I do have some recovery setup discs but the thing is I'm studying abroad and the discs cant be sent to me. Takes too long and its too expensive. I think it would be better to just install XP back again, my friend has the disc and he is willing to let me use it.

---

### Post by xeth_delta on 2008-01-21
I assume you are still able to boot Ubuntu. If that is the case, do the following.

Open a terminal / console and type:
```
sudo fdisk -l
```
this will list your available partitions. Please post the output of the command.
next, open /boot/grub/menu.lst and post the contents here, too.
```
gksudo gedit /boot/grub/menu.lst
```

Please post the contents between code tags (use the # button in the post window)

Xeth

---

### Post by DanielGJ5131 on 2008-01-21
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ac54ac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris


This is what I got when typing sudo fdisk -l

---

### Post by xeth_delta on 2008-01-21
> **DanielGJ5131 said:**
> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4ac54ac5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris


This is what I got when typing sudo fdisk -l

I am afraid it does not look good. I cannot see the NTFS partition in there. Please post also the output of:
```
sudo df -h
```
And please also the contents of "/boot/grub/menu.lst"

---

### Post by Sef on 2008-01-21
You might be able to recover your Windows with [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by DanielGJ5131 on 2008-01-21
sudo df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             106G  2.3G   98G   3% /
varrun               1003M   96K 1003M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M   88K 1003M   1% /dev
devshm               1003M     0 1003M   0% /dev/shm
lrm                  1003M   38M  966M   4% /lib/modules/2.6.22-14-generic/volatile
ile

---

### Post by rosegarden78 on 2008-01-21
I'm sorry if you lost any data as a result of this.  But when you install Ubuntu dual-boot you have to customize the primary disk partition.  It can be tricky at first for a casual user or n00b.

---

### Post by DanielGJ5131 on 2008-01-21
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

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ce7e7a7-1a0c-42c7-a2a3-6d5b507bef69 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ce7e7a7-1a0c-42c7-a2a3-6d5b507bef69 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title            XP
root             (hd0,0)
makeactive
chainloader      +1
savedefault

---

### Post by xeth_delta on 2008-01-22
> **DanielGJ5131 said:**
> ## e.g. lockalternative=true
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

## ## End Default Options ##

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ce7e7a7-1a0c-42c7-a2a3-6d5b507bef69 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2ce7e7a7-1a0c-42c7-a2a3-6d5b507bef69 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

title            XP
root             (hd0,0)
makeactive
chainloader      +1
savedefault

If you look at the contents of this file, you will notice that the windows partition is considered to be the same as the linux one, (hd0,0) or sda1.

There is something unusual, though. Your hard disk is supposed to around 120GB, but your "/" partition takes only 106GB:
```
sudo df -h

Filesystem Size Used Avail Use% Mounted on
/dev/sda1 106G 2.3G 98G 3% /
```

Where is the rest? Do you remember what steps you took when choosing what partition to use for linux?

One more thing I ask you to post:
```
sudo parted /dev/sda print
```

---

