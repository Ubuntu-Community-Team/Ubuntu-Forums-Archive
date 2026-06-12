---
title: "No boot? Chroot easy How-to"
date: 2015-08-01
forum: General Help
---

### Post by vidtek on 2015-08-01
I posted this on the Linuxmint forums last year, and had trouble finding it when I was asked for it yesterday.  Ubuntu forums are much more widely used and easier to access so here it is. 

No Boot-try this chroot solution

Post by vidtek on Wed Aug 13, 2014 5:10 pm
Sometimes after re-imaging I get no boot so if you are in the same situation try this:

You will have to do it from a live cd/dvd or usb stick but this must be the same architecture as installed environment ie-32 or 64-bit
and a chroot environment to make it work. run blkid or fdisk -l (that's small L - not the pipe symbol) as root to see which sd(x) is.

run this after ```
blkid
``` or ```
fdisk -l
```



   ```
 mount /dev/sdx /mnt
    mount --bind /dev /mnt/dev
    mount --bind /dev/pts /mnt/dev/pts
    mount --bind /sys /mnt/sys
    mount --bind /proc /mnt/proc
    chroot /mnt
```

Change sd(x) to your own drive sd(whatever).

# this gets you into your installed system, then you can run


   ```
 update-grub
```


and



    ```
grub-install /sdx
```


Get out of the chroot environment with cntl-d

and gracefully unmount


    ```
umount /mnt/dev/pts
    umount /mnt/dev
    umount /mnt/sys
    umount /mnt/proc
    umount /mnt
```


reboot.

I hope this helps some people who are stuck.

Tony
Gigabyte Z68XUD43B i7 16gb ram 5tb GTS450 1 x pcie hr2210 1 x TBS quad tuner 6205 64-bit Mint 17.1 & win 8.1 mce Be/FE myth 0.27 silicondust homerun dual network tuner.
Laptop Samsung NP R580 i5 nvidia linux Petra & win 8.1 mce

---

### Post by leunam12 on 2015-08-01
Thanks for the tutorial.
Question: why do you have to mount /dev/pts ? doesn't it mount automatically when you mount /dev ?

---

### Post by yetimon_64 on 2015-08-01
> **leunam12 said:**
> Thanks for the tutorial.
Question: why do you have to mount /dev/pts ? doesn't it mount automatically when you mount /dev ?

No it doesn't mount automatically from my experience, to get applications in the chroot working correctly I've always had to bind mount /dev/pts separately as instructed here.

I've noted if it is not mounted the directory is there but is empty, when you bind mount it the device files from the main OS are then used in the chroot.

---

### Post by vidtek on 2015-08-01
> **leunam12 said:**
> Thanks for the tutorial.
Question: why do you have to mount /dev/pts ? doesn't it mount automatically when you mount /dev ?

Leuman-

The Yeti answered for me, glad he did - I'd forgotten why!

One thing I didn't mention in the tutorial, occasionally error messages can occur about not finding /bin/bash I can't remember the details top of my head but it can be a real pain to do a work-around 

Tony.

---

### Post by oldfred on 2015-08-01
I have also seen this command just before the chroot /mnt

 sudo cp /etc/resolv.conf /mnt/etc/resolv.conf       #(may or may not be necessary to establish an internet connection)

And if a new UEFI system with sda1 as ESP - efi system partition:

sudo mkdir -p /mnt/boot/efi          #Create EFI partition mount point
sudo mount /dev/sda1 /mnt/boot/efi   #Mount EFI partition

And if a separate /boot:
sudo mount /dev/sda# /mnt/boot       #Mount boot (/boot) partition 
                                      (if separate from root partition)

---

