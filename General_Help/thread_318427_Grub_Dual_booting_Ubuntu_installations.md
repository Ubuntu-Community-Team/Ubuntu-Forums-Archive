---
title: "Grub: Dual booting Ubuntu installations"
date: 2006-12-14
forum: General Help
---

### Post by andrewski on 2006-12-14
I generally keep two installations of Ubuntu on my computer, current and current+1. I just upgraded to Feisty, and am looking to have it accessible in Grub when booting. Since each installation will update its own Grub file, I'd like to source them rather than edit one Grub file.

I tried loading the following in my Edgy grub file, but it doesn't work:
```
title Ubuntu Feisty
root (hd0,2)
chainloader +1
```I'm expecting that this will load Feisty's grub file, but instead it just says "GRUB" on the screen. Same goes for booting Edgy from Feisty's grub file.

Yes, Feisty is installed on /dev/sda3, so my Grub hd syntax is correct.

Any ideas?

---

### Post by hal10000 on 2006-12-14
It looks as if your grub in the feisty-installation was not correctly set up. So boot your edgy, chroot into your feisty, look into feisty's /boot/grub/menu.lst to check if it hss correct settings and call grub again:
After booting edgy, do:
```

sudo mount /dev/sda3 /mnt
sudo mount -t proc proc /mnt/proc -o rw,noexec,nosuid,nodev
sudo mount -t tmpfs udev /mnt/dev -o rw,mode=0755
sudo mkdir /mnt/dev/shm /mnt/dev/pts
sudo mount -t devpts /mnt/dev/pts -o rw,gid=5,mode=620
sudo mount -t tmpfs devshm /mnt/dev/shm

sudo chroot /mnt

```
After you have chrooted into feisty, do: [COLOR="Red"]grub[/COLOR] (this may take a time).
On the grub prompt do:
```

root (hd0,2)
setup (hd0,2)

```
This should work if your feisty's menu.lst is set up correct and if you have feisty's /boot directory on the same partition than its root-partition (/).

---

### Post by andrewski on 2006-12-14
> **hal10000 said:**
> 
```

sudo mount /dev/sda3 /mnt
sudo mount -t proc proc /mnt/proc -o rw,noexec,nosuid,nodev
sudo mount -t tmpfs udev /mnt/dev -o rw,mode=0755
sudo mkdir /mnt/dev/shm /mnt/dev/pts
sudo mount -t devpts /mnt/dev/pts -o rw,gid=5,mode=620
sudo mount -t tmpfs devshm /mnt/dev/shm

sudo chroot /mnt

```

This didn't work. I got an error on the 
```
sudo mount -t devpts /mnt/dev/pts -o rw,gid=5,mode=620
```either because the type or the device is missing. (I'm not sure which.) I tried saying "tmpfs devpts", but I'm not sure if that was the thing to do.

Anyhow, Grub failed for me when I tried to run those commands. My solution? Run grub-install to put Feisty's in the MBR, boot into it, and run those commands therein. I haven't rebooted since to test, but I'm hoping that will work.

---

### Post by hal10000 on 2006-12-16
Hi,
if your problem still exists, you can try sme things as above without mounting the devpts filesystem. I don't know if this is really needed, but on my system, if I try such things I always do this.

---

### Post by andrewski on 2006-12-17
Actually, get this: I just tried setting up each system without even chrooting; worked like a charm.
So, all told, here's what I did:
```
sudo grub
root (hd0,0)
setup (hd0,0)
root (hd0,2)
setup (hd0,2)
```I can switch between the two partitions' Grub prompts just fine.

"That was easy!"

---

