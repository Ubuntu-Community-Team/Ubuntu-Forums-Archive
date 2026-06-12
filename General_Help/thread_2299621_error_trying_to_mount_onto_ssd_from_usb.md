---
title: "error trying to mount onto ssd from usb?"
date: 2015-10-19
forum: General Help
---

### Post by joshgarciak20 on 2015-10-19
So i was following this [http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow](http://askubuntu.com/questions/254491/failed-to-get-canonical-path-of-cow)      because my surface wont boot from sdd even though the os says it's installed on my drive in one of the partitions. I get this error after inputing this:
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
sudo update-grub2


and it says 'cannot find a device for / (is /dev mounted?)
so, is there a way to fix this? i know that my os is on sda2 instead of 1 but other than that, i dont have a clue.

---

### Post by oldfred on 2015-10-19
UEFI or BIOS install?

Better to see lots of details:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

