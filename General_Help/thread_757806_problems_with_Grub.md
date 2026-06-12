---
title: "problems with Grub"
date: 2008-04-17
forum: General Help
---

### Post by agrab0ekim on 2008-04-17
Okay, so i got Ubutnu installed last night and was able to boot Vista and Ubutnu multiple times on their own (tested it)

now, today, i turned on my computer and get the following (right after the BIOS hello screen):

Grub Loading Stage1.5.

Grub Loading, please wait...
Error 22




what should i do?

---

### Post by mick8985 on 2008-04-17
Have you fiddled with boot device priorities or your bios in any way since the install?

---

### Post by bodhi.zazen on 2008-04-17
We need to boot a live CD and look at your hard drive and /boot/grub/menu.lst

show your hard drive with :

```
sudo fdisk -l
```

Mount your Ubutnu  partition at say /media/ubuntu and lets look at /media/ubutnu/boot/grub/menu.lst

---

### Post by mick8985 on 2008-04-17
> **bodhi.zazen said:**
> We need to boot a live CD and look at your hard drive and /boot/grub/menu.lst

show your hard drive with :

```
sudo fdisk -l
```

Mount your Ubutnu  partition at say /media/ubuntu and lets look at /media/ubutnu/boot/grub/menu.lst

Since he says that it doesn't reach the grub menu it would indicate that the the mbr isn't correctly pointing at /boot/grub , so I highly doubt the contents of menu.list are the issue

---

### Post by agrab0ekim on 2008-04-17
> **mick8985 said:**
> Have you fiddled with boot device priorities or your bios in any way since the install?

i have not fiddled with anything after that, though i did do a registry cleanning using CC... i dont think it is that, though not sure
when i get back i am planning on putting in my live CD and reinstalling the GRUB part, hopefully to fix it (side note, i will now always have my live CD with me)

---

### Post by bodhi.zazen on 2008-04-17
> **mick8985 said:**
> Since he says that it doesn't reach the grub menu it would indicate that the the mbr isn't correctly pointing at /boot/grub , so I highly doubt the contents of menu.list are the issue

From here : [http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)

> Quoted from the GNU/GRUB manual

    22 : No such partition
        This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk. 

For example there might be a mistake in the menu.lst file in the partition number, if there is no such partition as specified in the 'root (hdx,y)' line.
example,

```
title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,4)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=fe7bf845-7ce9-4733-b6de-f70f2b62076d ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
```

**Look at your partitions with your partitioning software or run 'sudo fdisk -lu' in a terminal and make sure you have the partition number correct here in your menu.lst boot entry.**

Bold added by me.

---

### Post by mick8985 on 2008-04-17
From the page you posted, this is the text immediately following your quote.
> 
This is also the error that people often see after they delete their Linux partition but they still have that partition's GRUB's stage1 written in the MBR.

They can easily cure that by overwritting the existing GRUB IPL code with code for another bootloader in another operating system.
In other words either re-install GRUB 
If the menu.list were the problem the boot menu would load then the error 22 would occur once you selected ubuntu, I was not trying to be confrontational just trying find the actual root of the problem.

---

### Post by bodhi.zazen on 2008-04-17
You have a good point and I was clarifying the grub error. I think we can easily identify the issue with the information I requested.

---

### Post by mick8985 on 2008-04-18
Yeah, I agree.

---

