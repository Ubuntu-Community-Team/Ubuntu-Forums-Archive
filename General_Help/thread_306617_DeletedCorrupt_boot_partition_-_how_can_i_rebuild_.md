---
title: "Deleted/Corrupt boot partition - how can i rebuild it?"
date: 2006-11-25
forum: General Help
---

### Post by BrowneR on 2006-11-25
Hi,
Having a few (major) problems here...

Earlier this morning i was running Edgy fine as I have been for some time now. Long story short I wanted to install a 3rd OS on my system and so I was rearranging some partitions on my drive so I could create another primary partition. (i know its dangerous)

My setup had a separate ext2 boot partition and ext2 root partition.

I was using Norton Partition Magic 8 to resize and move stuff about making one of my partitions an extended one so I could then create another primary partition. About an hour in it had resized my windows partition and moved my root partiton down the disk to free up space. [B]The tool then moved my separate boot partition and reported there were inode errors and aborted.

I now have a corrupt boot partition and am currently using the dapper live CD. (Grub fails with error 17)[/B] I have tried fsck.ext2 on my boot partition but it reports that it cannot find the superblock. I have tried specifying the default superblocks with the -b switch (8193, 16384, 32768 ) but its still fsck'd.

**I need to rebuild my boot partition. I can format the partition and install grub fine, that shouldnt be a problem. I was just wondering how I would go about copying over my kernel image? **

I presume I could boot from the live CD, then chroot into my existing root partition and then just apt-get reinstall my kernel? i would need walked through that procedure though. would it be ok to use the dapper live cd to rescue my edgy system?

Im going to reformat the partition now and install grub on it so i can at least then boot into windows and complete my repartitioning (fingers crossed).

Why oh why couldnt it have been my windows partition that sustained the errors :p

---

### Post by BrowneR on 2006-11-25
ok i have recreated the boot partition and installed grub meaning i can now boot to windows.

i cannot however boot into linux as i dont have the kernel image/initfs/vmlinux etc copied over to the boot partition.

i presume there is another copy of all this stored somewhere that i could just copy over?

tia

---

### Post by Rui Pais on 2006-11-25
why haven't you copied you vmlinuz first?

try to mount your system partition with a liveCD, check wich kernel version you have (ls /lib/modules should give that info)

download the version linux-image deb that match your libraries from [here]("http://packages.ubuntu.com").
and then extract what you need from there. Is the folder /boot* inside data.tar.gz, inside the deb.

(obvious i'm assuming that you have an ubuntu default kernel, not a manually builded one. 
In that case you would have a copy of kernel on /usr/src/<linux-version>/arch/i386/boot/)

---

### Post by BrowneR on 2006-11-25
ok thanks. i didnt copy vmlinuz first as i didnt know where to get a copy.

i have now extracted the kernel image (vmlinuz), system.map, kernel config and abi from the linux-image-2.6.17-10-generic_2.6.17-10.33_i386.deb (using dpkg-deb -x)

i copied these files to the root of my /boot partition and installed grub on there as well.

it all looks good.

the only thing i am sill missing is the initrd.img. i have to admid i have no itea what this is but i presume it is required to boot.

does anyone know where that can be found? i have checked in the package repository but cant find a corresponding deb.

---

### Post by BrowneR on 2006-11-25
ah wait i got it

chroot'ed off the live cd into the disk and ran

```
update-initramfs -c -k 2.6.17-10-generic

```

---

### Post by Rui Pais on 2006-11-25
he he :D you're fast.
I was thinking what can i suggest to put you in your system to run  the update-initramfs command... and completely forgetting the chroot trick (my Gentoo days are long gone.) 
I was to suggestion a boot on recovery mode, but chroot it's probably the best way.

Glad you remember first :)

---

### Post by BrowneR on 2006-11-25
only problem is... it doesnt boot :(

it seems to load the kernel (maybe?) but then i get the following output on screen
```
/bin/sh: can't access tty; job control turned off
(initramfs) [17179575.536000] usb 1-2: device not accepting address 2, error -71 
```
i am left at what apears to be a command prompt but i dont have permissions to access anything. i beleive i am just viewing the initramfs.

let me talk you through what i did so you can maybe find my error: from the live cd environment

[LIST]
[*]copied the kernel image to boot partition
[*]installed grub on boot partition
[*]mounted my root partition to /mnt/root
[*]setup chroot'd environment```
sudo su
mount /dev/sda2 /mnt/root/boot (mount boot partition)
mount -t proc none /mnt/root/proc (mount proc fs)
mount -o bind /dev /mnt/root/dev (remap dev tree)
chroot /mnt/root /bin/bash
```
[*]```
update-initramfs -c -k 2.6.17-10-generic
```
(initrd.img-2.6.17-10-generic now exists on boot partition)

[*] reboot!
[/LIST]

ok so that fails, not sure why?:-k 

maybe the chroot failed somehow and it created a ramfs for the live cd kernel which is different to mine?

or is it a permissions problem on the kernel image/initfs? i used root for them both i beleive.

would be helpful if you could post your menu.lst actually to make sure im calling the kernel correctly
```
#menu.lst

title winxp
root (hd0,0)
makeactive
chainloader +1
boot

title ubuntu
root (hd0,1)
kernel		/vmlinuz-2.6.17-10-generic root=/dev/sda4 ro quiet splash
initrd		/initrd.img-2.6.17-10-generic
savedefault
boot
```

maybe someone with the same kernel as me (edgy standard) could post their initrd.img as that should work for me also i beleive.

---

### Post by BrowneR on 2006-11-25
ok yet another silly mistake](*,) 
if i tell the kernel where the real root partition is (root=/dev/sda5) then it works! :D 
hahaha
i have spent so much time on this today! thanks for your help Rui its been a real learning experience.

---

### Post by Rui Pais on 2006-11-25
> **BrowneR said:**
> ok yet another silly mistake](*,) 
if i tell the kernel where the real root partition is (root=/dev/sda5) then it works! :D 
hahaha 
:lol: what's the famous sentence says? most computer errors happen between the keyboard and the chair... :) 
> i have spent so much time on this today! thanks for your help Rui its been a real learning experience.
What help? you solve practically everything alone. I just give you a link :D

Glad you have your system back to live,

have fun.

---

