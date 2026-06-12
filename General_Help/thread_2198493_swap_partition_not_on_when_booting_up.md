---
title: "swap partition not on when booting up"
date: 2014-01-09
forum: General Help
---

### Post by sketchy1poker on 2014-01-09
whenever i start up ubuntu 13.10, my swapfile is loading but the swap partition must be turned on manually. whenever i open GParted Partition Editor, i right click the linux-swap partition and have to manually set the swapon. is there a way to set this to automatically be on when i boot up? i am a total noob, not even sure if i am posting this in the right forum! decades of windows experience and almost no linux experience.

after i ran sudo blkid
```

/dev/sda1: LABEL="WINRE_DRV" UUID="508A648C8A647080" TYPE="ntfs"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="BC66-F3F6" TYPE="vfat"
/dev/sda3: LABEL="LRS_ESP" UUID="4A67-405D" TYPE="vfat"
/dev/sda5: LABEL="Windows8_OS" UUID="01CF0CED3C1008E0" TYPE="ntfs"
/dev/sda6: LABEL="recovery" UUID="01CF0CF75A89F600" TYPE="ntfs"
/dev/sda7: UUID="0d86cd58-407d-4761-8079-0d8660957150" TYPE="ext4"
/dev/sda8: UUID="e0f8f78c-1953-4189-9ab1-8481656e297b" TYPE="ext4"
/dev/sda9: UUID="a1189ec1-8022-4430-858c-1d64fd39e24b" TYPE="swap"
/dev/sda10: LABEL="LENOVO" UUID="12F67230F6721467" TYPE="ntfs"
/dev/sda11: LABEL="PBR_DRV" UUID="BA046DA0046D607D" TYPE="ntfs"
```

after i ran cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda6 during installation
UUID=0d86cd58-407d-4761-8079-0d8660957150 / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda2 during installation
UUID=BC66-F3F6 /boot/efi vfat defaults 0 1
# /home was on /dev/sda10 during installation
UUID=e0f8f78c-1953-4189-9ab1-8481656e297b /home ext4 defaults 0 2
# swap was on /dev/sda11 during installation
#UUID=a6c5376d-6e93-4b16-931e-8b66e26e1af5 none swap sw 0 0
/dev/mapper/cryptswap1 none swap sw 0 0
/swapfile none swap sw 0 0 
```

---

### Post by Impavidus on 2014-01-09
Add these lines to your /etc/fstab:```

#swap originally on /dev/sda9
UUID=a1189ec1-8022-4430-858c-1d64fd39e24b   none   swap   sw   0   0
```

---

### Post by rnerwein2 on 2014-01-09
hi
ups but take your own UUID !   :-))
ciao

---

### Post by sketchy1poker on 2014-01-09
> **Impavidus said:**
> Add these lines to your /etc/fstab:```

#swap originally on /dev/sda9
UUID=a1189ec1-8022-4430-858c-1d64fd39e24b   none   swap   sw   0   0
```

can you walk me through this? like i said, pretty much totally new, don't know how to do this particular thing. thanks for the reply and i hope it works!

---

### Post by Elfy on 2014-01-09
Open a terminal and get root rights. 

```
sudo -i
```

then we'll back up the file and then open the file for editing, be careful while you've got root rights

```
cp /etc/fstab /etc/fstab.0901
```

now open the file to edit it

```
gedit /etc/fstab
```

copy the lines from post #2 to the bottom of the file

```
#swap originally on /dev/sda9
UUID=a1189ec1-8022-4430-858c-1d64fd39e24b   none   swap   sw   0   0

```
then close gedit and save it when prompted, then close the root terminal

```
exit
```

All done.

---

### Post by sketchy1poker on 2014-01-09
thank you very much! that appears to have worked. now in gparted when i boot up the linux-swap is already on. the only other question i have might be a stupid question, but why does it say -- under the used and unused columns on the linux-swap in gparted?

---

### Post by Elfy on 2014-01-09
>  but why does it say -- under the used and unused columns on the linux-swap in gparted

it isn't here at the moment. 

Mine shows 4.00KiB being used.

---

### Post by sketchy1poker on 2014-01-12
i had to format and start over, having messed up my desktop beyond usability in my first installation of ubuntu. this wasn't a big deal because i wanted to start fresh and actually just rid my system of windows, and started from scratch with ubuntu. this made ubuntu run much better and a few issues have mostly disappeared, but now my swap is messed up yet again. i don't know what i did, i even made sure to set up the swap in the partition table when i ran installation and it looked like it was all working at first. after installing a bunch of software like chrome and codecs, java and the likes when you first install ubuntu, i opened gparted and my swap appears messed up again.


i have the following partition table in gparted (much easier to type out now)


/dev/sda1 fat32 /boot/efi 487mb 4.27mb used (boot)
/dev/sda2 ext4 / 37.25gb 7.38gb used
/dev/sda3 ext4 /home 875.16gb 24.41gb used
unallocated unallocated  18.63gb


i definitely had that last partition set up correctly (or so i thought) in the installation process, and also booted to a live usb drive and made sure to set it up properly in gparted. i rebooted, ejected the usb drive, booted back into my new installation of ubuntu, and the swap was STILL unallocated and not in use obviously.


what do i need to do? here are the results of the previous things people asked me to do in this thread to solve this problem previously


sudo blkid


/dev/sda1: UUID="2152-B1BC" TYPE="vfat" 
/dev/sda2: UUID="593f856a-b25e-4f25-ac48-3c5b00dcf7d9" TYPE="ext4" 
/dev/sda3: UUID="78b1b1a0-b721-4f52-8b17-b577bd573225" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="7c51619a-5ead-4e78-af2d-2900f3b4046c" TYPE="swap" 

cat /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=593f856a-b25e-4f25-ac48-3c5b00dcf7d9 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=2152-B1BC  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda3 during installation
UUID=78b1b1a0-b721-4f52-8b17-b577bd573225 /home           ext4    defaults        0       2
# swap was on /dev/sda4 during installation
#UUID=7c51619a-5ead-4e78-af2d-2900f3b4046c none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

---

### Post by sketchy1poker on 2014-01-12
well this is weird. i booted to live usb device and formatted the unallocated area as linux-swap again. i exited and rebooted, and now it does show up as linux-swap in gparted, but i get this when i do sudo blkid

/dev/sda1: UUID="2152-B1BC" TYPE="vfat" 
/dev/sda2: UUID="593f856a-b25e-4f25-ac48-3c5b00dcf7d9" TYPE="ext4" 
/dev/sda3: UUID="78b1b1a0-b721-4f52-8b17-b577bd573225" TYPE="ext4" 
/dev/sda4: LABEL="linuxswap" UUID="6493f3b9-d908-4644-bc79-7807db9f8a53" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="9b33ee92-f21f-4e07-b080-95ef59a62d1d" TYPE="swap"

am i supposed to have two swaps? i don't recall seeing this in my old swap issue.

any suggestions??? it wasn't on when i booted up either, but it's now showing as linux-swap in gparted like i said, instead of unallocated.

---

### Post by sketchy1poker on 2014-01-13
fwiw everything appears to be working ok. this is what i got when i ran free -h

             total       used       free     shared    buffers     cached
Mem:          5.0G       4.9G       121M         0B       7.5M       3.6G
-/+ buffers/cache:       1.3G       3.7G
Swap:          18G       346M        18G

---

### Post by Cavsfan on 2014-01-13
Glad to see you got it together.
An administrator on here, I think it was cariboo907, told me about using only one swap file, which I see you are doing so that is good.
Initially I had a swap file for every Ubuntu and had massive problems with fstab which you can imagine. #-o

I re-install sometimes but it is on the same partition that I had used previously so my /etc/fstab file never needs modifying. Plus my swapfile is always on sda2.
But, that is what you have to look at first when you have problems like that.
Glad to see Elfy helped out. :) There are a lot of people in this forum willing to spread their knowledge and help everyone. There is probably not a better forum out there.
I see you are dual booting or more; you might want to check out the grub tutorial in my signature. It makes things easier. I'm currently booting 6 Linux systems and Windows 7.

The last post shows what my current grub screen looks like right [_here_]("http://ubuntuforums.org/showthread.php?t=2076205&page=22&p=12896035#post12896035").

Not sure why but I think I could do without a swap file as it is never used at all:
```
cavsfan@cavsfan-MS-7529:~$ free -h
             total       used       free     shared    buffers     cached
Mem:          3.9G       2.7G       1.1G        25M       192M       1.4G
-/+ buffers/cache:       1.2G       2.7G
Swap:         1.0G         0B       1.0G
cavsfan@cavsfan-MS-7529:~$ 
```

---

### Post by sketchy1poker on 2014-01-14
i updated my status a few posts down on the first page. i don't dual boot anymore (on accident lol but it works out better this way anyway). here's what gparted looks like now

[IMG]http://i149.photobucket.com/albums/s59/sketchy1poker/gparted_zps44576e2a.jpg[/IMG]

another user on another forum suggested that this is what it should look like? i am not too sure anymore. all i do know is that ATM my ubuntu is running at least 2-3x better than when i was dual booting and had my swap set up so that it wasn't "unknown" and the swapon thing was on.

---

### Post by Elfy on 2014-01-14
> **sketchy1poker said:**
> well this is weird. i booted to live usb device and formatted the unallocated area as linux-swap again. i exited and rebooted, and now it does show up as linux-swap in gparted, but i get this when i do sudo blkid

/dev/sda1: UUID="2152-B1BC" TYPE="vfat" 
/dev/sda2: UUID="593f856a-b25e-4f25-ac48-3c5b00dcf7d9" TYPE="ext4" 
/dev/sda3: UUID="78b1b1a0-b721-4f52-8b17-b577bd573225" TYPE="ext4" 
/dev/sda4: LABEL="linuxswap" UUID="6493f3b9-d908-4644-bc79-7807db9f8a53" TYPE="swap" 
/dev/mapper/cryptswap1: UUID="9b33ee92-f21f-4e07-b080-95ef59a62d1d" TYPE="swap"

am i supposed to have two swaps? i don't recall seeing this in my old swap issue.

any suggestions??? it wasn't on when i booted up either, but it's now showing as linux-swap in gparted like i said, instead of unallocated.

> **sketchy1poker said:**
> fwiw everything appears to be working ok. this is what i got when i ran free -h

             total       used       free     shared    buffers     cached
Mem:          5.0G       4.9G       121M         0B       7.5M       3.6G
-/+ buffers/cache:       1.3G       3.7G
Swap:          18G       346M        18G
Hi - 2 things.

First it looks like you've got encrypted swap there - that'll be the cryptswap line.

Second - you've got an enormous amount of swap :)

You can bear that in mind in the future if you run out of disk space - but for now I'd just ignore it.

---

### Post by sketchy1poker on 2014-01-14
i'm not certain how i ended up w/ 18gig exactly, i know the first install guide suggested i have ~16gb. which seemed ok, even if it's too much, i'll never really need that extra 10-15gb or whatever it is.

---

