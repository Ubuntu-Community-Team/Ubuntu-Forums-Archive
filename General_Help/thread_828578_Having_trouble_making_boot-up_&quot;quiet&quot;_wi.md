---
title: "Having trouble making boot-up &quot;quiet&quot; without startup messages--help please?"
date: 2008-06-13
forum: General Help
---

### Post by caljohnsmith on 2008-06-13
I had some trouble with my Gutsy to Hardy upgrade, and I fixed it by manually installing the 2.6.24-16 kernel instead of trying to use the 2.6.24-19 kernel that came with the upgrade. So I manually added the 2.6.24-16 kernel to my /boot/grub/menu.lst as follows:
```
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=77677cb5-6e56-4936-a373-80c15de06bca ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

```
When booting into the 1.6.24-16 kernel, I get the kubuntu splash startup screen for several seconds that has the "oscillating" progress bar, but then when it is supposed to become the progress bar that shows the true percentage complete, it instead drops me into console mode and begins displaying all the startup messages. Then I finally get to the KDM and all is well until I log in, at which point it shows a strange looking KDE desktop progress screen that is quite different from the usual screen I'm used to seeing in Gutsy or from the Live CD. 

Any ideas what's going on? Do I need to reconfigure something? Thanks for any help.

---

### Post by caljohnsmith on 2008-06-15
In case anyone else has this problem, it is this bug here:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/205990)

Except in my case I had to modify an additional file not mentioned in that bug report. Here's the steps I used to solve it:

1. Make sure have the latest initramfs-tools
2. To see the new UUIDs:
```
sudo blkid -c /dev/null
```
3. Changed swap line UUID from /etc/fstab to match swap UUID from step 2. 
4. Changed UUID in /etc/initramfs-tools/conf.d/resume to match swap UUID from step 2.
5. Changed /etc/uswsusp.conf to have swap UUID in step 2
6. To update the initrd images with the new swap UUID:
```
sudo update-initramfs -u -k all
```
7. Restart

---

