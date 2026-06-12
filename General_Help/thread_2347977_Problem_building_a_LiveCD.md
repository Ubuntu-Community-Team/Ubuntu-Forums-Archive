---
title: "Problem building a LiveCD"
date: 2016-12-30
forum: General Help
---

### Post by David_Partridge on 2016-12-30
I followed the instructions here:

[//help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall]("https://ubuntuforums.org//help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall")

to build a Live DVD from my 16.04 LTS system.   It appeared to go very well, but when I tried to boot the ISO in a VM it said:

(initramfs) /cow format specified as aufs and no support found.

How to tweak this to use overlay which I understand is the currently favoured overlay mechanism instead of aufs?

root@Charon:/home/amonra# modprobe overlay
root@Charon:/home/amonra# lsmod | grep overlay
overlay                49152  0
root@Charon:/home/amonra# uname -r
4.8.13-040813-generic
root@Charon:/home/amonra# 

Thanks
Dave

---

### Post by kyknos12 on 2016-12-30
I know how to make [COLOR=#ff0000]Custom Ubuntu Based Distribution Direct From The PC[/COLOR], I have made earlier tutorial but the system of forum the moved The Jail, so do not know if may write post tutorial here

---

### Post by David_Partridge on 2016-12-30
I eventually found a web page that mentioned union= as a parameter for vmlinuz.

I changed /shared/livecd/cd/boot/grub/grub.cfg to look like:

```
set default="0"
set timeout=10

menuentry "Ubuntu GUI" {
linux /casper/vmlinuz boot=casper quiet splash union=overlay
initrd /casper/initrd.img
}

menuentry "Ubuntu in safe mode" {
linux /casper/vmlinuz boot=casper xforcevesa quiet splash union=overlay
initrd /casper/initrd.img
}

menuentry "Ubuntu CLI" {
linux /casper/vmlinuz boot=casper textonly quiet splash union=overlay
initrd /casper/initrd.img
}

menuentry "Ubuntu GUI persistent mode" {
linux /casper/vmlinuz boot=casper persistent quiet splash union=overlay
initrd /casper/initrd.img
}

menuentry "Ubuntu GUI from RAM" {
linux /casper/vmlinuz boot=casper toram quiet splash
initrd /casper/initrd.img
}

menuentry "Check Disk for Defects" {
linux /casper/vmlinuz boot=casper integrity-check quiet splash union=overlay
initrd /casper/initrd.img
}

menuentry "Memory Test" {
linux16 /boot/memtest86+.bin
}

menuentry "Boot from the first hard disk" {
set root=(hd0)
chainloader +1
}


```

and now I get: (initramfs) /cow format specified as overlay and no support found.

which is a step forward, BUT how do I get the kernel load to issue a modprobe for overlay?

Dave

---

### Post by David_Partridge on 2017-01-01
Looking at the casper code I'm rather confused as why that panic was issued!

```

    # Confirm the final format was valid.
    if [ "${UNIONFS}" != "unionfs-fuse" ]; then
        modprobe "${MP_QUIET}" -b "${UNIONFS}" || true
        if cut -f2 /proc/filesystems | grep -q "^${UNIONFS}\$"; then
            :
        else
            panic "/cow format specified as ${UNIONFS} and no support found"
        fi
    fi 


```

amonra@Charon:/usr/share/initramfs-tools/scripts$ modprobe overlay
amonra@Charon:/usr/share/initramfs-tools/scripts$ cut -f2 /proc/filesystems | grep overlay
overlay
amonra@Charon:/usr/share/initramfs-tools/scripts$

Are any of the casper developers able to assist?

Cheers
Dave

---

### Post by David_Partridge on 2017-01-02
I finally found the solution to the problem. 

When running the chroot part of the install, part of the procedure is to run [FONT=courier new]update-initramfs -u -k $(uname -r)[/FONT] to build the initrd.img.

Unfortunately overlay.ko isn't a default part of the 4.8.13 kernel (and I think also not part of the 4.4.0 kernels), so I had to change file /shared/livecd/work/rootfs/etc/initramfs-tools/modules so that it would include overlay into the initramfs:

```

[FONT=courier new]# List of modules that you want to include in your initramfs.
# They will be loaded at boot time in the order below.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
overlay[/FONT]

```

Once that was done, I re-ran the update-initramfs under the chroot and rebuilt the image.

The new ISO image booted nicely!

Dave

---

### Post by sudodus on 2017-01-02
Congratulations and thanks for sharing your solution :-)

---

### Post by David_Partridge on 2017-01-02
Now I have to work out why I can't login ...

I'll open another thread.

Dave

---

