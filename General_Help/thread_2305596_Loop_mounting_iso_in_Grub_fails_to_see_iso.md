---
title: "Loop mounting iso in Grub fails to see iso"
date: 2015-12-07
forum: General Help
---

### Post by flocculant on 2015-12-07
So - if I add a folder to boot for images

/boot/iso then add this to /etc/grub.d/40_custom

```
menuentry "xenial 64bit" {
set isofile="/boot/iso/xenial-desktop-amd64.iso"
loopback loop (hd0,7)$isofile
echo "Starting $isofile..."
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash
initrd (loop)/casper/initrd.lz
}
```

Everything works fine

If I have the image elsewhere it fails to boot, saying it can't find the file

```
menuentry "xenial 64bit" {
set isofile="/mnt/Images/XubuntuImages/Xenial/xenial-desktop-amd64.iso"
loopback loop (hd0,8)$isofile
echo "Starting $isofile..."
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash
initrd (loop)/casper/initrd.lz
}
```

I must be missing something - perhaps you can see it :)

---

### Post by coffeecat on 2015-12-07
Silly question, but...

Is your /mnt folder in a different partition from your /boot folder? I see you have (hd0,7) for /boot, but (hd0,8) for /mnt.

---

### Post by flocculant on 2015-12-07
heh - you got here before me - a wander to the kitchen and the light came on - both physically and figuratively :)

Thinking about it - /mnt's not going to be a thing till the machine has booted. 

> Is your /mnt folder in a different partition from your /boot folder? I see you have (hd0,7) for /boot, but (hd0,8) for /mnt. No. But /mnt/foo was a different partition than /

I originally had the 'images' on a different drive altogether (hd1,2) that just never worked locally. 

What I've done now is create a folder on / and had to own it for me - I need the images to not end up being owned by root, causes havoc with zsync. 

For the record what's working currently is 

```
menuentry "xenial 64bit" {
set isofile="/Images/Xenial/xenial-desktop-amd64.iso"
loopback loop (hd0,7)$isofile
echo "Starting $isofile..."
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=${isofile} quiet splash
initrd (loop)/casper/initrd.lz
}
```

What I would much prefer is to fight grub into submission and have it work with (hd1,2) though.

---

### Post by oldfred on 2015-12-07
Path is one of the major issues, I often even just experiment until I got it right.

And yes no mounts from Ubuntu exist when loading ISO. And boot drive is always hd0. So if directly booting sdb then it still is hd0. But if booting from sda it is hd0 and sdb will be hd1.

My case was even worse. I had skipped a port in SATA. My sda was always hd0 when booting from it, but my flash drive, normally sdf, would become sdb and every drive got renumbered. And I boot from sdc or sdd, so sda was hd1, flash drive was hd2. If that makes sense to you then you understand it better than me. :)

On my hard drives I just create a new partition with one folder so path is drive (hdX,Y)/ISO.

And because I always forget to run sudo update-grub on changes, I now just add one entry to 40_custom using a configfile to a text files in my ISO folder with my grub2 boot entries.

```
menuentry 'Live ISOs' {
configfile (hd2,4)/iso/livecdimage.cfg
} 

```

Above is booting my sdb drive when booting from sdc or sdd and iso folder is in partition 4.
And liveimage.cfg is all my boot stanzas for every ISO in /iso.

---

