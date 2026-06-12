---
title: "cant boot windows or ubuntu on two hdds"
date: 2006-11-29
forum: General Help
---

### Post by person123 on 2006-11-29
i have a huge problem. i have windows on the master drive and i tried to install ubuntu on a slave drive and where it tells me to install grub i used the default (hd0) and now whenever i turn on my comp all it does is give me a grub error 17. i read all the other posts about this error but i dont have a windows boot cd or boot disk to fix anything and now i am stuck on the live cd. thank you to anyone that can help me](*,) ](*,) ](*,) ](*,)

---

### Post by daniminas on 2006-11-29
Error 17 : Cannot mount selected partition

This happend when grub can't recognize the type of the file sistems.


When grub load the menu try:

grub> find /boot/grub/stage1
//supouse it return (hd0,4) 

grub> root (hd0,4)

grub> kernel /vmlinuz root=/dev/hda* ro
// /dev/hda* will be (hd0,4) in this case /dev/hda5

grub>boot

---

### Post by daniminas on 2006-11-29
press 'c' to see the grub shell.

and to load windows:

grub> root hd(0,0)
//depend where you have the installation
grub> makeactive
grub> chainloader +1
grub> boot

---

### Post by daniminas on 2006-11-29
And then, with ubuntu loaded:

sudo grub

grub> find /boot/grub/stage1
//supouse it return (hd0,4)

grub> root (hd0,4)
 Filesystem type is xfs, partition type 0x83

grub> setup (hd0)
//or setup (hd0,4) if you want to preserve your MRB
grub> quit

Good luke

---

### Post by person123 on 2006-11-29
i think i made it worse before everything i tried to install everything again but this time instead of hd0 i typed in hdb then it said it cant install grub and something about a fatal error. i rebooted the comp and now it says grub loading then grub error 18. i am really new to linux and ubuntu and i have no clue what i am doing once i get my xp back up and running i wont even try to use ubuntu again

---

### Post by person123 on 2006-11-29
sorry about the double post but i there a way to delete grub and ubuntu and just go back to how windows booted before?

---

### Post by daniminas on 2006-11-29
From GNU grub doc:

18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

---

### Post by person123 on 2006-11-29
i decided that i will reinstall ubuntu on the slave drive and grub in the hd0 thing just to get back to square one. and if anyone can help me thank you so much

---

### Post by daniminas on 2006-11-29
I think is a bios error.. :-k 

Still, try mount your partition from the live cd (mount /dev/hda0 /mnt)

sudo grub
grub> find /boot/grub/stage1
grub> root(hd0,2)
grub> setup(hd0)
grub> quit

---

### Post by person123 on 2006-11-29
i typed in "mount /dev/hda0 /mnt" into the terminal thing nd it gave me "special device /dev/hda0 does not exist"

---

### Post by daniminas on 2006-11-29
> **person123 said:**
> i decided that i will reinstall ubuntu on the slave drive and grub in the hd0 thing just to get back to square one. and if anyone can help me thank you so much

hda0 is whew i have installed ubuntu, depend of where you have installed ubuntu...

---

### Post by person123 on 2006-11-29
can someone give a tutorial or something to maybe fix the grub thing so i could get windows to start im not very used to the interface of ubuntu

---

### Post by Giselle on 2006-11-29
Post the output of:
```

sudo fdisk -l

```

I'm a bit confused as to your disk setup right now.

---

### Post by person123 on 2006-11-29
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1             578        9729    73513440    7  HPFS/NTFS
/dev/hda2               1         577     4634721    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/hdb: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        7009    56299761   83  Linux
/dev/hdb2            7010        7064      441787+  82  Linux swap / Solaris
/dev/hdb3            7065        7301     1903702+  83  Linux

---

### Post by Giselle on 2006-11-29
This might get you in to windows. You never know though, I'm very tired :(

1. Reboot your computer. When you get to the GRUB menu (where you select the OS to boot) hit c to open the command line.

Run these commands:

2. root (hd0,1)
3. chainloader +1
4. boot

Try this and hope it works. If not post here what it says and i'll try and work it out.

---

### Post by person123 on 2006-11-29
but it doesnt even let me get into the menu it say loading then something about 1.5 then or something like that, then it give me an error "grub error 17"

---

### Post by Giselle on 2006-11-29
Somehow I missed that :X

You could try daniminas' advice and reinstall grub from the live cd. His commands tailored to your setup:

sudo mount /dev/hdb1 /mnt

sudo grub
grub> root(hd1,0)
grub> setup(hd1)
grub> quit

p.s. make sure your BIOS is set to boot from the drive with the ubuntu install

---

### Post by person123 on 2006-11-29
tried it out but this is what i get when i put setup (hd1)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

---

### Post by Giselle on 2006-11-29
grub> find /boot/grub/stage1

Run that in the grub command line. Then run the 

grub> root (hdx,y)
grub> setup(hd1)
grub> quit

where x and y are the numbers find outputted.

---

### Post by person123 on 2006-11-29
when i type in find /boot/grub/stage1 it give me "file not found"
i think i messed up my comp bad

i was reading other posts and it looks to me like i installed the grub thing into my windows thing? and all the other people seemed to fix it with a simple floppy boot thing but i dont know anyone with a computer to make a boot disc is there a way i can make on with the live cd ubuntu

---

### Post by geek_Man on 2006-11-29
I would recommend the Super GRUB Disk. You can do a number of things with it. You'll also be able to into Linux with it. The link is [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/") 
You should give it a try.

---

### Post by person123 on 2006-12-01
:-D  thanks i was able to boot windows but now i can only boot windows through the cd but that is fine for now

---

### Post by geek_Man on 2006-12-02
You can also fix your original MBR if you want. Along with temporarily change certain things in your menu.lst file so that you can boot into Ubuntu. Glad it helped!

---

### Post by pseudologically on 2006-12-07
[Repairing Damaged MBRs and Boot Sectors in x86-Based Computers]("http://www.microsoft.com/technet/prodtechnol/winxppro/reskit/c28621675.mspx#EJ5AE")

---

