---
title: "Extracting bootable image from USB drive"
date: 2007-09-24
forum: General Help
---

### Post by Githlar on 2007-09-24
OK, I've been messing with creating a multi-boot USB flash drive using floppy/hard drive images and memdisk. I was finally able to make my favorite Boot CD, Hiren's BootCD, boot from a flash drive. Now, my problem is that I had to resize the partition in order to make it boot. So, I've got a lot of free space on the end.

I usually use dd to create an image of what I'm doing. This is usally fine, but I now have a working disk that I have to back up. I want to be able to use dd to extract it to a harddrive image, HOWEVER, I don't want all that free space on the end to be in the image. In a sense, I want to resize the image to the size needed without losing any data or the MBR needed to boot the files.

Anybody know a tool that can do this?

---

### Post by Githlar on 2007-09-24
I'm going to rephrase this one more time in a, perhaps, more understandable way:

I really only want to back up that one partition, but at the same time keep it bootable.

So, I want to be able to use the end product disk image in qemu as the first hard drive.

---

### Post by Githlar on 2007-09-24
Hmm... Theoretically, couldn't I find the start and end addresses of the free space, open the image in a hex editor and cut it out. I'd also have to somehow locate the part that defines the disk size and edit that to fit the new size I think.

---

### Post by vanadium on 2007-09-24
partimage does backup partitions without including empty space. Otherwise, if you would prefer to use dd, try compressing the image. I guess that the empty space would compress very well in a way that you would end up with a relatively small backup. The command to do that would probably go like

dd if=<yourpartition> | gzip > ddimage.gz

---

### Post by Githlar on 2007-09-24
But you can't boot straight from the partition. I tried that. You need to get the MBR of the disk too.

---

### Post by Githlar on 2007-09-24
I hexed the file and it doesn't seem as straight-forward as it sounds. So, scratch that idea.

---

### Post by Githlar on 2007-09-24
I tried just extracting the partition with dd and booting it with memdisk, but qemu told me "Invalid system disk." I figured this would happen if it didn't have a boot sector.

---

