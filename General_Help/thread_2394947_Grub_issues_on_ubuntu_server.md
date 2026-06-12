---
title: "Grub issues on ubuntu server"
date: 2018-06-24
forum: General Help
---

### Post by giulio-coslo on 2018-06-24
Hello to everyone
I hope I posted in the correct section.
I have an HP Microserver with few VMs on it.
One of theese has Ubuntu server and it's intended for file sharing through the computers in the house.
It mounts automatically a RAID partition and controls the access to folders in this RAID partition by managing few accounts. Everything easy.
Last day after ubuntu updates it won't show grub menu anymore.
I get a screen with "Minimal BASH-line editing is supported...."
I'm able to boot with a live .iso and I took a screen to show the partitions tree.
[https://www.dropbox.com/s/hxup24vjcz4ws89/LVM%20ubunru%20server%20microserver.jpg?dl=0](https://www.dropbox.com/s/hxup24vjcz4ws89/LVM%20ubunru%20server%20microserver.jpg?dl=0)
Can anyone help me to restore grub functionallity?
I tried few ways found on the Net but I come always to the grub bash screen.
Tell me if you need something else.

Best regards

---

### Post by TheFu on 2018-06-24
I'd boot off the same version in a live-boot flash/dvd, run fsck against all the partitions to fix any issues. Assuming that goes well, next setup a chroot using the partitions on the HDD (put them into the proper place), then reinstalled grub and update grub.  That should fix it unless there is a HW issue.

The chroot methods can be found lots of places.  Usually there is a bind mount for /dev/ and /proc/ which is how you know it is doing all the stuff you need for grub to work correctly.

OTOH, if you have solid backups, this is the time to use those, since most people setup their restore process to be pretty easy.  If you don't have solid backups, now is the time.

---

### Post by giulio-coslo on 2018-06-25
Hello
Thanks for the reply.
I have few backups but they are old. Nevertheless I wanted to learn something trying to repair the boot (I can reinstall everything if I want - maybe I'll have to do it).
I tried fsck but everything looked nice.
Then I tried this way:

```
sudo vgdisplay
sudo vgchange -ay fs01-vg
sudo mkdir foo
sudo mount /dev/fs01-vg/fs01--vg-root foo
sudo mount /dev/fs01-vg/fs01-vg-root foo
sudo mount /dev/fs01-vg/root foo
sudo mount /dev/sda1 foo/boot
sudo mount -obind /dev foo/dev
sudo mount -obind /dev/pts foo/dev/pts
sudo mount -obind /proc foo/proc
sudo mount -obind /sys foo/sys
sudo chroot foo
```

Then:

```
sudo grub-install --boot-directory=foo/boot /dev/sda
sudo update-initramfs -u -k 4.13.0-39-generic
sudo update-grub
```

With theese commands I found errors on 4.13.0-36 who was missing physically so I purged it. Then everything looked nice.
At the end, after I unmounted everything and rebooted the VM I'm back at the grub page that says:  "Minimal BASH-line editing is supported...."
Nothing looks changed.
Did I miss something?

Thank you

---

### Post by TheFu on 2018-06-25
Would have been nice if you mentioned using LVM and provided the lsblk, lvs,vgs, and pvs output.

Inside the chroot, you only see /boot, not foo/boot.  That is an error. The chroot should have included /boot, methinks. I've never used a device to specify a bind-mount and some of the other commands seem incorrect too. For example,  I can't remember ever needing to include pts in the chroot and
What are these about? 
```
sudo mount /dev/fs01-vg/fs01--vg-root foo
sudo mount /dev/fs01-vg/fs01-vg-root foo
sudo mount /dev/fs01-vg/root foo
```
 Only 1 should be needed.

Looks like the instructions you found were either for something else or the translation to your system particulars failed.
Or I could be wrong.

---

