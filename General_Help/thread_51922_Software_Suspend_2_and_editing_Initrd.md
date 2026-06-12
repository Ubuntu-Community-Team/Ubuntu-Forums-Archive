---
title: "Software Suspend 2 and editing Initrd"
date: 2005-07-25
forum: General Help
---

### Post by pr00f 0f d3f on 2005-07-25
I usually just search around online and the forums until i find an answer to my problem, but this one has me stumped (hence this is my first forum post).

Yesterday i put ubuntu on my dell inspiron 1000 laptop; everything works fine, except for sleep to ram and sleep to disk, which hangs the system -- just like it does on every other dell laptop, as i've noticed. Looking around online, i found that while the built-in acpi support doesn't work with dell laptops, people have had success with Software Suspend 2. so, i patched the kernel source, it compiles, done. When i use the custom kernel, i now have this error:

> Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

this is to be expected, since in the [How to](http://www.suspend2.net/HOWTO-7.html#ss7.4) they state:
> If you are using an initrd, you MUST edit the linuxrc script to attempt to resume before filesystems are mounted. Do this by inserting the line:

echo > /proc/software_suspend/do_resume

somewhere after mount /proc but before mounting filesystems in your linuxrc script.

If you are using an initramfs, you will need to do the same thing to your /sbin/init script, else you will never be able to resume.

i assume this is the problem, but i'm not sure how to edit the init scripts in ubuntu, or where to put that command. any suggestions?

I apologize if this is in the wrong section

---

### Post by jesse on 2005-07-25
Have a look at this. 

[http://www.ubuntuforums.org/showpost.php?p=231552&postcount=13](http://www.ubuntuforums.org/showpost.php?p=231552&postcount=13)

I got the exact same kernel panic error when trying to reboot after simply upgrading the "linux-image" package when prompted to do so by the Ubuntu update manager. 

I solved it, and now can boot my system again, because I followed the instructions in the linked post above almost exactly. 

To quote: 

"boot from live cd

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

change source list into Breezy.

apt-get install initrd-tools
apt-get remove linux-image-2.6.10-5-686

it will remove 2.6.10 and install linux-image-2.6.12-2-686 .
Of course, I think it is still beta version..
but at least I can boot my system."

I booted from the live cd (not to be confused with the installation cd) and did 

mkdir /mnt/linux
mount /dev/hda1 /mnt/linux
chroot /mnt/linux /bin/bash
mount -t proc /proc /proc

Then, without closing the root terminal, I typed either 

apt-get install initrd-tools 
or 
apt-get upgrade initrd-tools 
(I don't remember)

Then I navigated to /mnt/linux/etc/apt/sources.list and added the breezy repositories to sources list 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse


Then in the same root terminal I typed

apt-get update
apt-get install linux-image

This presented me with a list of possibilities, so I selected 2.6-12 I think

apt-get install linux-image-2.6-12 etc (I don't remember exactly what it was named)

Then I rebooted and had no more kernel panic. 

Upon rebooting the first time a light-bulb icon next to the update manager prompted me to reboot again to finish setting up the new kernel. I haven't had another kernel panic since.

---

