---
title: "dual-boot howto?"
date: 2013-07-31
forum: General Help
---

### Post by twsLeGR on 2013-07-31
I am already running Ubuntu 13.04 and would really like to install Puppy Linux Slacko alongside it? Help anyone please.

---

### Post by GwL3eNC on 2013-07-31
Hi!

Ok, thats much, could be easy or a bit harder. I dont know puppy, therefore i dont know if It's setup is
so easy like the ubunu setup. If you got first windows and then you install ubuntu, grub does
everything automaticly for you. Possibly puppy also.  Just try out, find free place on one of
your  drives or resize your partition with gparted. After installation you have to configure the
grub loader to tell him about puppy. the grub-customizer tool simplifys the usage.

[https://launchpad.net/~danielrichter2007/+archive/grub-customizer](https://launchpad.net/~danielrichter2007/+archive/grub-customizer)

Linux is often try, try and try again. Keep your important data first, then you got
nothing to loose.

---

### Post by poncho2 on 2013-07-31
I think you might be able to install puppy first then when you install ubuntu it will detect puppy and give you the bual boot option.

---

### Post by oldfred on 2013-07-31
I installed an older copy of Puppy. I just used another partition and installed into it. I have several 25GB partitions I use for test installs. Do not remember if I had issues with its boot loader or not. But from grub2 in my Ubuntu I just ran this and it found Puppy.
sudo update-grub

If install gives choice on where to install grub2's boot loader, probably best to not install or install to the new Puppy partition (usually not recommended to install to partition). Then reboot into Ubuntu and update from that. Otherwise you may get Puppy's boot loader as the one in control of booting all systems.

Found this in my notes, but new version may be a lot different:

 I did have to move lupu-511.sfs to the top level of the partition ( same as /boot not inside /boot) and created /boot/lupu511 with all the other files including vmlinux & initrd.gz.
```
menuentry "Puppy 511" {
    insmod part_msdos
    insmod ext2
    set root='(hd2,msdos12)'
        linux /boot/lupu511/vmlinuz root=/dev/ram0 pmedia=atahd loglevel=7 pkeys=us 
        initrd /boot/lupu511/initrd.gz
}
```

---

