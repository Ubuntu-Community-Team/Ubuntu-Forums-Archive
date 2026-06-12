---
title: "Restored Disk Image (DD) But No Grub2 Menu - Boots Direct to Win10"
date: 2016-01-10
forum: General Help
---

### Post by Alan5127 on 2016-01-10
I decided to move my laptop Windows install from Win8.1 to Win10 last week.

Before doing so, I created a full disk image of the HDD (/dev/sda) using DD.

I then clean installed Win10, followed by Ubuntu 15.10, and as expected when the laptop booted, I got the GRUB2 menu, from where I could choose either Win10 or Ubuntu 15.10.

While configuring Win10, I realised I wanted to replicate some settings from Win8.1, so I imaged the HDD with Win10 / Ubuntu 15.10 on it using DD, restored the Win8.1 image, booted into Win8.1 and copied the settings I wanted, then restored the Win10 / Ubuntu 15.10 image of the HDD.

The restore seemed to work perfectly, but when I boot the laptop, it boots straight into Win10, without the GRUB2 menu coming up.

Two questions:

1) What (might) have I done wrong?

2) Can I fix without completely wiping Ubuntu, and reinstalling it?

Thanks,

Alan.

---

### Post by Bucky Ball on 2016-01-10
[Boot Repair]("https://help.ubuntu.com/community/Boot-Repair") is your friend. 

Run the bootinfoscript and post the link to the output back here, please. You can also run a recommended repair or go to the 'Advanced' tab and choose to install grub to sda.

---

### Post by Alan5127 on 2016-01-12
Hi,

Boot-repair fixed the issue perfectly.  I let it run the recommended fix, and all was good.

In terms of what went wrong, I had thought that doing a dd image of the entire hard disk (sda), then later restoring that image, would bring the machine back into the exact same configuration it was in when the image was created.

Am I wrong about that, or is it possible that I did something wrong when creating the image:

The command I used was:

```
sudo dd if=/dev/sda conv=sync,noerror bs=64K | gzip -c > sda.img.gz
```

To restore, I did:

```
 gunzip -c sda.img.gz | dd of=/dev/sda
```

Thanks,

Alan.

---

### Post by Alan5127 on 2016-02-02
I am going to mark this as solved, and re-post the more general question regarding what does and does not get imaged using DD.

Thanks,

Alan.

---

