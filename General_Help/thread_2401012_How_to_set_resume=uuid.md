---
title: "How to set resume=uuid"
date: 2018-09-12
forum: General Help
---

### Post by danielsender on 2018-09-12
Since I had to change the HD in my Dell Dimension 1100, running 18.04, I am having a problem shown during updates as:

```
W: initramfs-tools configuration sets RESUME=UUID=6752bc85-87bd-4f55-a01d-d966557ff115W: but no matching swap device is available.
I: The initramfs will attempt to resume from /dev/sda5
I: (UUID=eb8347d0-623b-4b9a-95f1-da527c084617)
I: Set the RESUME variable to override this.



```

but I did set the new UUID in /etc/fstab and in /etc/initramfs-tools/conf.d/resume - is there anywhere else that I have to touch?

Thanks

---

### Post by #&amp;thj^% on 2018-09-12
On mine early on in Development I had changed  "/etc/initramfs-tools/conf.d/resume"
To 
```
RESUME=NONE
``` 
or you could just comment the line (by putting a # in the beginning of the line)

---

### Post by danielsender on 2018-09-12
When I change that file, is there any activation that I have to process prior to 'update-initramfs'? Or I have to reboot?

---

### Post by #&amp;thj^% on 2018-09-12
Yes, thanks for pointing that out. >>It's been a long time ago since I had done that so my old memory forgot to add that. ;)
```
sudo update-initramfs -u
```  
I would still reboot also.

---

### Post by danielsender on 2018-09-12
I did comment that line in /etc/initramfs-tools/conf.d/resume and did update-initramfs -u but I'm still getting the same message - Isn't there some other file that keeps spitting out that old UUID?

---

### Post by #&amp;thj^% on 2018-09-12
In going back to my old notes I keep I had tried to solve this with "/etc/default/grub" BUT that did not solve it for me.

So I then did the steps I had already shown you in post#2

But lets give this a whril then:
```
sudo blkid
```
Now here on mine it shows for swap:
```
UUID="b007b23d-e1b5-40de-a8fb-dc2d89f83347"
```
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a device; this may
# be used with UUID= as a more robust way to name devices that works even if
# disks are added and removed. See fstab(5).
#
# <file system>             <mount point>  <type>  <options>  <dump>  <pass>
UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347 swap           swap    defaults,noati$
UUID=ed5a7d7e-281d-48d6-a50c-e9705c769a63 /              ext4    defaults,noati$

/dev/disk/by-uuid/09771289047AED44 /mnt/09771289047AED44 auto nosuid,nodev,nofa$
/dev/disk/by-uuid/25B65825105A7849 /mnt/25B65825105A7849 auto nosuid,nodev,nofa$
/dev/disk/by-id/usb-SanDisk_Ultra_4C530001050423123075-0:0-part2 /mnt/usb-SanDi$


```
So just now to be sure it works here at least:
```
sudoedit /etc/fstab
```
Save and close.
Now add your UUID>>>>and again here:
```
sudoedit /etc/initramfs-tools/conf.d/resume
```
Save and close.>>And for good measure run:
```
sudo update-initramfs -u -k all
```
Fingers Crossed

---

### Post by danielsender on 2018-09-12
Yeah, I had all this done - /etc/fstab as well as /etc/initramfs-tools/conf.d/resume have the correct UUID and I did 'sudo initramfs-update -u -k all' but it keeps giving the same message. I was wondering, is it necessary to run 'mkswap /dev/sda5' besides the editing on the files above?

---

### Post by #&amp;thj^% on 2018-09-13
The only way for me to see the warning on my end is to remove the file in "/etc/initramfs-tools/conf.d/resume"
As seen:

```
 sudo update-initramfs -u -k all
[sudo] password for me: 
update-initramfs: Generating /boot/initrd.img-4.18.5-041805-lowlatency
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347)
I: Set the RESUME variable to override this.
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347)
I: Set the RESUME variable to override this.
update-initramfs: Generating /boot/initrd.img-4.15.0-31-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347)
I: Set the RESUME variable to override this.
update-initramfs: Generating /boot/initrd.img-4.15.0-29-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347)
I: Set the RESUME variable to override this.
update-initramfs: Generating /boot/initrd.img-4.15.0-26-generic
I: The initramfs will attempt to resume from /dev/sda2
I: (UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347)
I: Set the RESUME variable to override this.
```

Now after i recreate the file "/etc/initramfs-tools/conf.d/resume":
```

 sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.18.5-041805-lowlatency
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-29-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-26-generic
```
All is good.
Now if I change to "RESUME=NONE"
```
sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.18.5-041805-lowlatency
W: initramfs-tools configuration sets RESUME=NONE
W: but no matching swap device is available.
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
W: initramfs-tools configuration sets RESUME=NONE
W: but no matching swap device is available.
update-initramfs: Generating /boot/initrd.img-4.15.0-31-generic
W: initramfs-tools configuration sets RESUME=NONE
W: but no matching swap device is available.
update-initramfs: Generating /boot/initrd.img-4.15.0-29-generic
W: initramfs-tools configuration sets RESUME=NONE
W: but no matching swap device is available.
update-initramfs: Generating /boot/initrd.img-4.15.0-26-generic
W: initramfs-tools configuration sets RESUME=NONE
W: but no matching swap device is available.

```
But when I add the UUID like:
```
RESUME=UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347
```
I now show:
```
 sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-4.18.5-041805-lowlatency
update-initramfs: Generating /boot/initrd.img-4.15.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-29-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-26-generic
```
Maybe check for typeo's in both "etc/fstab" and in "etc/initramfs-tools/conf.d/resume"
I'll post mine just for reference only: "etc/fstab"
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=b66538cb-b17b-4e11-b2eb-e7c049d2f762 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347 none            swap    sw              0       0
```
Now "/etc/initramfs-tools/conf.d/resume"
```
RESUME=UUID=b007b23d-e1b5-40de-a8fb-dc2d89f83347
```

---

### Post by danielsender on 2018-09-13
I found what the problem was: generally whenever I modified some parameter(s) in a configuration file and just for my records, I create another file with the extension "*orig*", so in this case I placed in the same folder (*/etc/initramfs-tools/conf.d*) a file called *resume.orig* with the old UUID. Apparently, the program update-initramfs does not look at the exact name of the file but reads whatever is in that folder or to any file that starts with the characters "*resume*", so it kept reading the old file even though it wasn't called "*resume*". So I just removed *resume.orig* and the problem went away.

Thank you very much for your time and effort.

Daniel

---

### Post by leiti34 on 2019-07-03
Thank You!

---

