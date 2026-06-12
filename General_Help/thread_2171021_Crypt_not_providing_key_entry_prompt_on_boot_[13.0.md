---
title: "Crypt not providing key entry prompt on boot [13.04]"
date: 2013-08-28
forum: General Help
---

### Post by Ninkul on 2013-08-28
Nope, I'm just an idiot. Apparently I needed to install the package even though it was already accessible. Although, my computer's display driver is crashing on boot now but that's something I can probably look into myself.


> Hi,

I've recently been interested in creating an encrypted portable USB drive that automounts on boot (don't ask why). For some reason I can't seem to get it to work on a fresh install of ubuntu.

Currently, I'm unable to input my key after setting up /etc/fstab and also /etc/crypttab on a fresh install. I've tried the same method on debian netinst (had to apt-get a few packages) but it seemed to work fine. On boot I'm currently seeing:
[B][I]Keys: Disk drive for /media/ndrive is not ready yet or not present.
Continue to wait or press s to skip mounting or M for manual recovery.[/I][/B]

I've tried typing my crypt key on this prompt to no avail.

After pressing "s" I see another "***Keys: ***" appear afterward.


This is what I'm doing:
1) Install Ubuntu
2) Identify USB drive with "sudo blkid" (/dev/sdb1)
3) sudo cryptsetup luksFormat /dev/sdb1
4) Test "sudo cryptsetup luksOpen /dev/sdb1 ndrive"
5) Check status "sudo cryptsetup luksOpen /dev/sdb1 ndrive"
6) Make mountpoint "sudo mkdir /media/ndrive"
7) Mount "sudo mount -t auto /dev/sdb1 /media/ndrive -o default,noatime"
8) Update fstab, "sudo nano /etc/fstab" add "/dev/mapper/ndrive /media/ndrive auto default,noatime 0 0"
9) Create crypttab, "sudo nano /etc/crypttab" add "ndrive /dev/sdb1 none luks,timeout=30"
10) Correct permissions "sudo chmod 0744 /etc/crypttab"
11) Turn off "quiet" and "splash" "sudo nano /boot/grub/grub.cfg", comment out "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" and add below "GRUB_CMDLINE_LINUX_DEFAULT="

Any help would be appreciated. My next step is to maybe try 12.04.

---

