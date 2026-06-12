---
title: "Install medium changes after booting computer from it"
date: 2020-05-09
forum: General Help
---

### Post by bydo on 2020-05-09
I hope someone can explain the following puzzling thing.

I downloaded lubuntu-20.04-desktop-amd64.iso and successfully wrote it to an 8GB USB flash drive. Afterwards I verified it using the following script that I devised a long time ago and have used many times:

```
head -c $(stat -c %s lubuntu-20.04-desktop-amd64.iso) /dev/sdb | pv -s $(stat -c %s lubuntu-20.04-desktop-amd64.iso) | md5sum && pv lubuntu-20.04-desktop-amd64.iso | md5sum
```

The two checksums matched. However, lsblk showed that the flash drive had two volumes on it: sdb1 and sdb2. Is this normal?

Next, I successfully booted into Lubuntu on a UEFI computer using the flash drive and then shut down the computer as normal. I then re-verified the flash drive and discovered that the checksum had changed. Also, lsblk now showed that the flash drive contained **three** volumes: sdb1, sdb2 and sdb3.

I repeated this with a different ISO image: this time xubuntu-20.04-desktop-amd64.iso. Exactly the same things happened.

I then repeated it with a Debian ISO image (debian-live-10.3.0-amd64-xfce+nonfree.iso) using the same flash drive. This time there was only one volume the whole time and the checksum didn't change, proving that there's nothing wrong with my flash drive.

So please can someone explain why the Lubuntu and Xubuntu images showed two and then three volumes on the flash drive, and booting a computer from them caused them to change?

---

### Post by Impavidus on 2020-05-10
How did you make the live usbs? Did you use persistance?

---

### Post by bydo on 2020-05-10
> How did you make the live usbs?
$ sudo dd if=lubuntu-20.04-desktop-amd64.iso of=/dev/sdb bs=1M

> Did you use persistance?
No.


I invite you or anyone else to do as I did and write one of the ISO images to a USB flash drive, check the MD5 checksum using the command I gave, boot a computer from the drive and then check the MD5 checksum again. See whether you have the same result.

---

### Post by &amp;KyT$0P# on 2020-05-11
Could it be related to [this]("https://ubuntuforums.org/showthread.php?t=2431843")?  Does it still happen if you boot the live system with [FONT=Courier New]nopersistent[/FONT] boot parameter?

---

### Post by bydo on 2020-05-12
> **halogen2 said:**
> Could it be related to [this]("https://ubuntuforums.org/showthread.php?t=2431843")?[FONT=Courier New][/FONT]

Yes, thank you.

I don't know why it couldn't have been mentioned in the release notes. It seems like a significant change.

---

