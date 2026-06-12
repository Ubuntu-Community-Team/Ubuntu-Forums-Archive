---
title: "Data Recovery on a Galaxy S3 using Ubuntu"
date: 2013-05-02
forum: General Help
---

### Post by pmains on 2013-05-02
Hi. I've been trying to recover data erased during a factory reset of my Galaxy S3.

My plan is
(1) Root my device
(2) Mount the device on an Ubuntu computer
(3) Use dd to create an image of my phone's internal memory
(4) Use a tool like Scalpel to recover data in the image

I am stuck at step 1. I used the following guide: [http://galaxys3root.com/galaxy-s3-root/how-to-root-galaxy-s3-on-linuxubuntu/]("http://galaxys3root.com/galaxy-s3-root/how-to-root-galaxy-s3-on-linuxubuntu/") When I tried to run heimdall, I got the error: "heimdall ERROR: Failed to initialise protocol!"

What does this mean? I tried restarting the device, putting it into USB Debug mode and starting over again, but to no avail. Heimdall failed again and again. What am I doing wrong?

(The scalpel part of my solution came from [http://android.stackexchange.com/questions/15869/how-can-i-recover-a-deleted-file-on-android]("http://android.stackexchange.com/questions/15869/how-can-i-recover-a-deleted-file-on-android") )

---

### Post by Mark Phelps on 2013-05-02
The main problem you're going to have is that Google removed USB Mass Storage from their OSs starting with ICS, and is continuing that with JB.

There SHOULD be ways to mount the filesystem now using MTP, but I and others have tried this to great lengths -- and have NOT been able to get it to work.  I have had to resort to mounting it using MTP in Win7 -- where the Samsung device drivers help a lot.

I've read that this has been "fixed" in Ubuntu 13.04 -- but haven't had time to install it and try it.  You could try booting from a LiveUSB of 13.04 and seeing if you can then mount the SGS3.

---

### Post by pmains on 2013-05-02
Thanks. 

Have you tried go-mtpfs?  ( [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html) ) Without rooting, I  was able to mount the device to /media/MyAndroid as the tutorial suggested,  but was unable to then make an image of the device. It's been a while since I made a disk image with dd, but it seems like it's telling me it needs the actual device (/dev /*) rather than a mounted folder. 

Are you saying that making an image will be impossible even if i do root due to the mass storage issue you describe?

---

### Post by pmains on 2013-05-02
It just occurred to me - the mtab file probably will tell me what in dev corresponds to media/MyAndroid. That's where I should have been dding from,  yes?

---

### Post by tgalati4 on 2013-05-02
Would it be easier to put a large, blank, micoSD card in the phone, then use the built-in backup routine to dump the image to the SD card then pull the card and operate on it using an SD card reader in Ubuntu?

---

### Post by phoinx on 2013-12-05
I'm passing through the same steps pmains did - trying to create an image from my Samsung Note II internal memory (dumbly called SD card in the device), so I can try to recover data later.

I used go-mtpfs to mount it on /media/myAndroid. The device "path" is "DeviceFS(GT-N7100)", but I can't use it to dump an image (dd if="DeviceFS(GT-N7100)"... won't work).

Is there a device path for it I could use?

---

