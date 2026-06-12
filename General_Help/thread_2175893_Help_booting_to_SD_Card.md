---
title: "Help booting to SD Card"
date: 2013-09-21
forum: General Help
---

### Post by P_THE_AWESOME on 2013-09-21
So I installed XBMCbuntu 12.2 (Intel-Nvidia) on my 8GB Class 10 SDHC Card on my Samsung NP-N310 netbook. It installed successfully (from a USB drive that I booted into) but I soon realized that there is not option in the BIOS to boot to the SD Card. The BIOS is up-to-date.

I found a great post here: [http://ubuntuforums.org/showthread.php?t=986126&page=3&p=11915401#post11915401](http://ubuntuforums.org/showthread.php?t=986126&page=3&p=11915401#post11915401)


The problem is that it does not go into details. I booted into Linux Secure Remix 13.0.4 from another USB drive and had my other drive ready to boot into. I got to Step I, #5:
> Add the required modules to support the SD-card at the start of Linux (after GRUB 2 passes over the control)
Edit the file      Code:
     ```
/etc/initramfs-tools/modules 

```by adding these module names:
(On other hardware/Linux the required modules might differ For my system with Ubuntu 12.04 these modules have done the job.)
     Code:
     ```
mmc_block
sdmod 

```
Is that path for the Linux Secure Remix or my SD Card? How can I edit it with gedit in the right permissions? What about all of the other paths in the post?

I noticed that at that path on both the SD Card and Linux Secure Remix had another SD Card-related line that acted as an example (commented out):
```

#raid1
#sd_mod

```
Should I use "sd_mod", "sdmod", or both?

Also, what exactly is the "Alternative Solution" referring to? Lastly, how do I do some of the other [more complicated] things said in the post?

Thanks for any help!
I would have posted this on that thread, but it was closed.

---

### Post by sudodus on 2013-09-21
Try both alternatives (one of them each time)! Let us hope one of them works :-)

---

### Post by P_THE_AWESOME on 2013-09-22
Thanks, but I can't do anything until I know what that path is referring to and how to edit it correctly. Please re-read my entire post.

---

### Post by P_THE_AWESOME on 2013-09-22
I'm starting to think... **Is this really worth the trouble?** Should I just get a USB SDHC Card Reader?

---

### Post by sudodus on 2013-09-22
If you want fast booting from removable media, please consider a USB 3 pendrive. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

