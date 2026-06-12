---
title: "Grub2 chainloading ISO boot loader?"
date: 2016-03-13
forum: General Help
---

### Post by josh168 on 2016-03-13
So there is a lot of information out there, and I am not too sure if I have been sorting through it effectively. I feel like I am headed in circles with my research.

I just resolved a previous thread in which I was trying to boot the Windows 10 installer and receiving error 17.

Now I am trying to boot Linux distro iso images. Just the regular iso files you download for any given distro. So far I've been booting them, successfully, into their live environments. I had some trouble with GParted and Clonezilla, but after I found I needed to use 'union=overload boot=live isofrom=/iso-images/file.iso' they both worked pretty easily.

My issue is that I'd prefer to boot from the iso files' boot menus. Particularly for distros like ubuntu, but I can only boot directly to the desktop. Is it possible for me to chainload from grub2 to grub2/syslinux/etc when the secondary boot code is inside an iso file?

I hope I am making sense, I don't know how else to explain.

---

### Post by oldfred on 2016-03-13
Each distribution requires different boot parameters.
If you do not know at all what is required, you can mount ISO and look at syslinux or grub.cfg for correct parameters.
       [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I do not think it is possible to chain load. The ISO is a special case and the grub1 loopmount command mounts the ISO for grub's use. If you chain to a grub inside the ISO, it does not know it is loopmounted, and paths to all the files will not be the default as if it was configured for an install flash drive.

Some installs that do not work with loopmount require you to extract kernel & boot files and use that to boot. Once booted then you can configure to use ISO for rest of system. I have not done that, so do not know details.

---

### Post by goofprog on 2016-03-13
There is a tool called "YUMI" is creates a multiboot usb from ISO files.
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

---

### Post by josh168 on 2016-03-13
> **oldfred said:**
> 
I do not think it is possible to chain load. The ISO is a special case and the grub1 loopmount command mounts the ISO for grub's use. If you chain to a grub inside the ISO, it does not know it is loopmounted, and paths to all the files will not be the default as if it was configured for an install flash drive.

That is unfortunate. Couldn't I manually edit some of that stuff? Or would loading the config file be the primary issue I'd need to deal with?

> **goofprog said:**
> There is a tool called "YUMI" is creates a multiboot usb from ISO files.
[http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

Exactly what I am trying to do, except that mine will hopefully work whereas my experience with YUMI has been: I'm lucky if it works. Even with "supported" distros, YUMI is hit or miss. I don't have the resilience to debug something as much of a blackbox to me as YUMI is. I actually started all this with YUMI, then multibootusb-7.5.0, and then tried to hack a combination of the two together. When that didn't work, I took things into my own hands. I've made faster progress than when I was using either of them. Multibootusb actually wasn't too bad, but I couldn't get windows to work with it.

---

### Post by yancek on 2016-03-13
> My issue is that I'd prefer to boot from the iso files' boot menus.

Why?  If you want to boot to Safe Graphics or have the other options, you will need to put them in the main grub.cfg you are booting from.  A couple of examples booting an Ubuntu iso below.  You can see the second entry has different options.  I don't know any other way to do this.

> menuentry "Ubuntu Live 14.04 32bit" {
    loopback loop /ubuntu-14.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz boot=casper  iso-scan/filename=/ubuntu-14.04-desktop-i386.iso quiet splash --
    initrd (loop)/casper/initrd.lz
}

menuentry "Ubuntu Live 14.04 32bit Safe Graphics Mode" {
    loopback loop /ubuntu-14.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz boot=casper  iso-scan/filename=/ubuntu-14.04-desktop-i386.iso quiet xforcevesa splash --
    initrd (loop)/casper/initrd.lz
}


> Is it possible for me to chainload from grub2 to grub2/syslinux/etc when the secondary boot code is inside an iso file?

You can chainload from Grub2 to another Grub2, Grub2 to Grub Legacy and the reverse and also to syslinux on installed systems.  I can't think of any way that would be possible to do with an iso boot or even with an extracted/copied iso to a partition.  The method of booting is different and a standard boot will look for code in a specific location on the partition 
and it won't be there.

Not all Linux distributions/tools are capable of being booted directly from an iso file but almost any should be able to boot if you first loop mount them, then copy the extracted files to your partition and get a proper entry in the grub.cfg file.

---

