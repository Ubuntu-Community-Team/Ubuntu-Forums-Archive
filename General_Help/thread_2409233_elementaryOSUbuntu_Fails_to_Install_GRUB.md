---
title: "elementaryOS/Ubuntu Fails to Install GRUB"
date: 2018-12-30
forum: General Help
---

### Post by slooksterpsv on 2018-12-30
Hello All,

I had an issue that was making it difficult to install Ubuntu or elementaryOS to my HP Pavilion x360. I wanted to post what I did, in hopes that it would help someone else out. Here's what would happen:

1) Install Ubuntu or elementaryOS and it would fail at the end with a GRUB fatal error.
2) Rebooting the system would enter the GRUB safe mode where you don't get to select an option.
3) Reinstalling Windows and trying to install again would yield the same result as #2 though this time it would default to booting into Windows, but anytime ubuntu was selected from EFI it would fail.

The way I figured out to resolve this was very touch and go. Essentially, here's what I did.

1) Install Ubuntu until it gets to the error.
2) Reboot
3) Mount Ubuntu drive to /mnt and mount EFI drive to /mnt/boot/efi
4) Perform bindings for proc, sys, dev
5) chroot into /mnt
6) Connect to WIFI and remove USB thumb drive (just pull it out)
7) Run update-grub and wait
8) Run grub-install /dev/sda and wait (if it takes longer than 30 seconds, just hit CTRL+C)
9) Reboot

I'm thinking step 8 can be skipped as I believe update-grub fixes the issue. EIther way, that's how I was able to fix it. I'm successfully running elementaryOS on an HP Pavillion x360 with 4GB RAM and 500GB HDD. Everything is working too. Hope this helps.

---

### Post by slooksterpsv on 2019-03-28
Had to run through this again and it worked. Something with the USB being mounted causes an issue with Grub not updating.

---

