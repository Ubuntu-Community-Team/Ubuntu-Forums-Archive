---
title: "How to  boot into chroot"
date: 2013-01-02
forum: General Help
---

### Post by predato on 2013-01-02
I have 64 bit Natty, I need to run 32 bit version of it because of dial-up modem not running due to proprietary driver licence. 
I set up a 32 chroot in my system. I want to boot into it at grub menu. Because since chroot use system's kernel modules I can not install 32 bit driver in chroot. 
My question is how can I boot into chroot at system startup?
I know it's possible but there is not much documentation. Here is a guy that managed it, but he didn't explain it step by step. [http://superuser.com/questions/450024/making-grub-boot-into-chroot-directory](http://superuser.com/questions/450024/making-grub-boot-into-chroot-directory)
Please help.
Thank you

---

### Post by dino99 on 2013-01-02
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
[http://ubuntuforums.org/showthread.php?t=1898835](http://ubuntuforums.org/showthread.php?t=1898835)

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by predato on 2013-01-02
> **dino99 said:**
> [https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
[http://ubuntuforums.org/showthread.php?t=1898835](http://ubuntuforums.org/showthread.php?t=1898835)

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
First of all thank you very much for the post, it's hard to get answer here. Unfortunately it's not what I asked for. I want to create a menuentry at grub2 and choose it at boot screen to boot into chroot I created. Similar to that 
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM).
Thank you

---

### Post by 3Miro on 2013-01-02
You can set a dual-boot system with both 32-bit and 64-bit architecture and select between them at boot (from the Grub menu). This is called "dual-boot", search around there are plenty of tutorials on how to set it up.

Chroot is different thing altogether. Chroot will let you use the same kernel with two different installations at the same time. While the two installations can be of different architecture (i.e. one can be 64-bit and the other 32-bit) and you can use chroot to run 32-bit software under 64-bit system, ultimately it will not help with drivers. Drivers are specific to the kernel and chroot used only one kernel.

---

### Post by predato on 2013-01-02
> **3Miro said:**
> You can set a dual-boot system with both 32-bit and 64-bit architecture and select between them at boot (from the Grub menu). This is called "dual-boot", search around there are plenty of tutorials on how to set it up.

Chroot is different thing altogether. Chroot will let you use the same kernel with two different installations at the same time. While the two installations can be of different architecture (i.e. one can be 64-bit and the other 32-bit) and you can use chroot to run 32-bit software under 64-bit system, ultimately it will not help with drivers. Drivers are specific to the kernel and chroot used only one kernel.

3Miro, thanks, your explanation is satisfactory. I don't know if you read the stuff in the link at  my first post, I still wonder if chroot can be turned into an installation by replacing 32 bit kernel modules into /var/chroot/boot and adding grub menuentry to pick up at boot screen.

---

### Post by dino99 on 2013-01-02
you still need to understand what chroot is, and redefine your way; your request is a non sense.

---

### Post by predato on 2013-01-02
better yet this link [http://unix.stackexchange.com/questions/43283/boot-into-chroot-directory-leaves-the-root-partition-read-only](http://unix.stackexchange.com/questions/43283/boot-into-chroot-directory-leaves-the-root-partition-read-only)
answer is below the page

---

### Post by 3Miro on 2013-01-02
> **predato said:**
> better yet this link [http://unix.stackexchange.com/questions/43283/boot-into-chroot-directory-leaves-the-root-partition-read-only](http://unix.stackexchange.com/questions/43283/boot-into-chroot-directory-leaves-the-root-partition-read-only)
answer is below the page

I see what they are doing in the link, but I don't understand why and how it relates to your problem. They are simply saving themselves couple of commands at boot time.

With or without chroot you can only run one kernel at a time. That kernel is either 32-bit or 64-bit. The kernel can only use its own 32-bit or 64-bit drivers, you cannot even mix and match kernel modules that have been compiled for two different 64-bit kernels (or 32-bit for that matter). For example, you cannot take drivers compiled for Fedora and use them under Ubuntu, even if both have been compiled for the same version and architecture.

You cannot use the driver from your 32-bit Natty installation and run it on any other kernel or newer installation.

---

### Post by predato on 2013-01-03
I know, I must install 32bit into another partition. Apart from that; now that I set up a 32bit chroot, can I use it as 32 bit installation? I lack of disk space. I read that it's possible to install two linux distros into the same partition. Thank you again for responding

---

### Post by cwsnyder on 2013-01-03
The only way that I have seen or heard for having 2 distros in one partition is to have one of them a Virtual Machine, which, **NO**, can't be booted to from GRUB, but has to have the host machine installed first.

It works like WUBI/Mint4Win.

---

### Post by predato on 2013-01-03
> **cwsnyder said:**
> The only way that I have seen or heard for having 2 distros in one partition is to have one of them a Virtual Machine, which, **NO**, can't be booted to from GRUB, but has to have the host machine installed first.

It works like WUBI/Mint4Win.

But I can boot into  live iso image stored in my primary linux partition and according to above link it seems possible. But I have grub 2 installed, if I had legacy grub I could try it. In Grub2 I managed to boot into iso image by following menuentry 
menuentry "UBUNTU ISO" {
set isofile="/boot/iso/ubuntu-12.04.1-desktop-i386.iso"
loopback loop (hd0,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

---

### Post by cwsnyder on 2013-01-03
A Live CD iso is a self-contained, non-updating, non-changing image on the drive.  You can make changes for the Live session, but they do not persist past a reboot.  Booting into that type of image is EXACTLY the same as booting from a CD in your CD drive.

To have 2 WORKING and updating installations, the 'second' installation is going to have to be virtualized.

---

### Post by predato on 2013-01-03
> **cwsnyder said:**
> A Live CD iso is a self-contained, non-updating, non-changing image on the drive.  You can make changes for the Live session, but they do not persist past a reboot.  Booting into that type of image is EXACTLY the same as booting from a CD in your CD drive.

To have 2 WORKING and updating installations, the 'second' installation is going to have to be virtualized.

I think I was misunderstood. I don't want boot into both of them and run at the same time. I wondered if it's possible to turn a chroot into a distro installation as a guy managed it in a different linux distro in the link. Thank you all.

---

### Post by predato on 2013-01-08
This link provide us with a solution about booting into subdirectory. I post it as a reference [http://unix.stackexchange.com/questions/39423/boot-linux-system-from-a-subdirectory-on-a-partition](http://unix.stackexchange.com/questions/39423/boot-linux-system-from-a-subdirectory-on-a-partition)

---

