---
title: "grub2 disaster recovery"
date: 2014-06-22
forum: General Help
---

### Post by roadtest on 2014-06-22
Hello,

One of my ubuntu 12.04 is a vm on vmware ESXi host. It has separate boot and root partition. One developer did fsck on the live root partition by mistake and this vm can only boot to initramfs mode  with some errors - "/proc is not found".  My understanding is root partition inode table was damaged causing read error. This might be fixed by fsck the root partition.  Since I don't have access to the ESXi host directly( I can't mount this VM root partition from another host), the only option is using the grub to boot vm with nfs root partition. Here is what I did:

The grub version is 1.99-21ubuntu3.14

grub> set
?=0
color_highlight = ..
color..
default=0
feature_timeout_style=y
have_grubenv=true
linux_gfx_mode=text
menu_color_hi...
menu_color_normal..
pager=1
prefix=(hd0,msdos1)/grub
recordfail=1
root=hd0,msdos1
grub> insmod normal
grub> lsmod  <=there is no NFS in lsmod output
Name...
minicmd
linux
vbe
video_fb
mmap
relocator
help
ls
affs
afs
afs_be
befs
befs_be
btrfs
lzopio
cpio
fat
hfs
hfsplus
iso9660
jfs
..
pxe
lvm
..
grub>ls (hd0,1)/     <=from output, it seems my /boot partition is not damaged and all kernel/initrd files are accessible
abi-2.6.32-38-server vmcoreinfo-2.6.32-38-server config.. system.map-... grub/ abi-.. initrd.img-.. vmlinuz-... memtest.. vmlinuz..
grub> linux /vmlinuz root=/dev/nfs nfsroot=<nfs.server.ip>:/opt/shares/boot ip=<this vm IP>   <=here I am trying to set the nfsroot with following error
**error: no such disk.**
grub> linux (hd0,1)/vmlinuz-3.2.0-30-generic root=/dev/nfs nfsroot=<nfs.server.ip>:/opt/shares/boot ip=<this vm IP>
grub> initrd (hd0,1)/initrd.img-3.2.0-30-generic
grub> boot
.....after a while with booting message
**ALERT! /dev/nfs does not exist. Dropping to a shell!**
busyBox v1.18.5....
(initramfs)

Is it possible to set the nfsroot from grub? Is above failure related to  no nfs module in "lsmod" output in grub?  Maybe there is better way to fsck root partition without doing the nfsroot? It seems the version I am using doesn't have bootp or tftpboot command, which give me the option to point to the boot server.

Thanks in advance!

carl

---

### Post by roadtest on 2014-06-23
I recovered the system by updating the initrd-img file with nfs module in it.  Then I am able to netboot the instance with nfsroot.  I am happy bird again!

Cheers,

carl

---

