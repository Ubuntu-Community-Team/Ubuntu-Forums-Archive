---
title: "help with ubuntu live iso after booting from grub2"
date: 2013-08-21
forum: General Help
---

### Post by hotshot247 on 2013-08-21
i'm trying to boot an iso from another partition using grub2 and i can boot it right and everything but the ubuntu login screen shows up. it makes me sign in which it's supposed to go straight into the OS on a live cd. i googled it and it says to try to enter the username: ubuntu and the password is blank and that didn't work then somebody said that my image is bad which i redownloaded it and still doesn't work so i was thinking that it might be a problem with my code. i am wondering if somebody will help me check out my code and see if it's right. here is what i have in the 40_custom file:

```
menuentry "Ubuntu 13.04 Desktop I386" {
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set E50C-166A
    loopback loop /ubuntu-13.04-desktop-i386.iso
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-13.04-desktop-i386.iso quiet splash locale=en_US bootkbd=us console-setup/layoutcode=us user-setup/encrypt-home=true noeject --
    initrd (loop)/casper/initrd.lz
}
```

thanks in advance for the help!

---

### Post by VMC on 2013-08-21
Here's mine that work:

```
menuentry "ISO" {
    set root='(hd1,msdos1)'
    set isofile="/ISO/kde-saucy-desktop-amd64.iso"
    loopback loop (hd1,msdos1)$isofile
    linux (loop)/casper/vmlinuz.efi boot=casper maybe-ubiquity iso-scan/filename=$isofile noprompt noeject
    initrd (loop)/casper/initrd.lz
  }
```

I had problems with Kubuntu and adding "maybe-ubiquity" solved the loopback livecd issue.

---

### Post by oldfred on 2013-08-21
Some of mine. I have a folder /iso in a gpt partitioned drive that is seen as hd2 and partition 4. Note that some of the 64 bit versions now use vmlinuz.efi. I have to insmod the gpt partitioning so it will work with that. MBR(msdos) should just work, but you can insmod that.
Boot drive is always hd0, and with my system additional drives are then in port order. I normally boot sdc, so sda becomes hd1 and sdb is hd2. But if I directly boot sdb then it is hd0.

```
menuentry "Ubuntu 13.10 Saucy ISO 64bit" {
    set isofile="/iso/saucy-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/xubuntu-13.04-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

