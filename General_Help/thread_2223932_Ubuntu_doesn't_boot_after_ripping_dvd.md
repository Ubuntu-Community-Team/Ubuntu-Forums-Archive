---
title: "Ubuntu doesn't boot after ripping dvd"
date: 2014-05-13
forum: General Help
---

### Post by monkeybrain20122 on 2014-05-13
Hi,

I have Ubuntu 14.04 installed in an external hard disk for testing. Last night I was ripping a dvd with handbrake and fell asleep. This morning when I woke up I saw the ubuntu login screen (unity greeter) I entered my password repeatedly but unable to login. So I shut down the machine, reboot it and removed the dvd then tried to boot off the external drive, still no luck. I saw black screen, no grub, no nothing. 

So I removed the external hard drive, booted into Ubuntu 13.10 which is my working system and is installed in the internal hard drive. Then attached the external drive and viewed it in gparted. It complained that the /home partition of 14.04 has "unknown file system' with a big black or red mark. So apparently somehow I toasted the /home partition with my dvd burning.

I then reformatted the /home and restored it with an image but still wouldn't boot. I then booted into 13.10 again, mounted the 14.04 / partition and reinstall grub and now it works.

I am wondering what could have happened?

---

### Post by oldfred on 2014-05-13
You may have been able to fix it with a e2fsck. Any abnormal shutdown can cause issues.
Did you have enough space for DVD? If you filled that could also be an issue.

If you created a new partition it would have a new UUID. So to correctly mount a new /home you would have to update fstab with new UUID.

---

### Post by monkeybrain20122 on 2014-05-13
Hi, I have a lot of space for the DVD so it can't be the issue (almost 200G free space)

uuid is fine as it goes with the image no matter what I do with the actual partition.

---

