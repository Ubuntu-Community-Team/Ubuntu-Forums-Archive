---
title: "Mounting the iso, copying files, then create another iso"
date: 2008-03-19
forum: General Help
---

### Post by lolpcx on 2008-03-19
```

mount ubuntu.iso -o loop -t iso9660 /mnt/ubuntu
mkdir cdroot
cp -r /mnt/ubuntu/* cdroot/
cd cdroot
mkisofs -r -N -ldots -d -D -J -V "the ubuntu cd" -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -x lost+found -o ../cool.iso .

```

It does create a cool.iso, if i burn it into a cdrom it does boot normally, i can see the ubuntu boot loader screen asking me what i want to boot (start/install the livecd, use vesa and stuff), until this part everything is fine and nice. But then when i pick to start the livecd, it loads somethings...and then it stops in initramfs ! I've tried many things, but nothing seems to work.

If you have the iso of ubuntu there, try that out and tell me why it does not complete the boot.

Ok, if you did not get what i am trying to do, i am mounting the iso of ubuntu, copying everything into a folder, telling mkisofs it is bootable, and where is the isolinux.bin, then creating a .iso which works fine until it drops me to a shell (initramfs).

I want to do that because I am studying, thanks.

---

### Post by Diabolis on 2008-03-19
That looks a lot like the steps that take to customize the live-cd.
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

### Post by lolpcx on 2008-03-19
No. I am studying the boot thing by trying to boot both damnsmallinux and ubuntu in one cd. That is made by changing the isolinux.cfg. Do I have to do all those steps for that ? I want the live the way it is man, i don't want to change anything :/

I didn't even add damnsmallinux yet, just copied the files of /mnt/ubuntu to a folder and used mkisofs to generate the iso.

To make it simplier, all i really need is to mount it, copy, and create the iso, isn't it possible ? That should take me two minutes only, not all those steps on Live CD Customization, because I don't really want do do any customization.

It worked with damnsmallinux, i mounted the iso, copied to a folder, created the iso and burned. I am trying both of them separately in the first hand, just to make sure one doesn't mess with the other, it's a problem i'd have to face later. Ubuntu is mounted, copied, created the iso and burned alone yet, and still it doesn't pass initramfs.

---

### Post by jcmb on 2008-03-19
I am having the same issue with Xubuntu. I am following the instructions from the "Ubuntu Hacks" book for customizing the Ubuntu Live CD.

---

### Post by pointone on 2008-03-19
What error messages appear when it fails to boot? Is it dropping to a BusyBox shell? Please be more detailed.

---

