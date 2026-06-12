---
title: "Busy UUID when booting"
date: 2015-10-12
forum: General Help
---

### Post by cearlp on 2015-10-12
I am running ubuntu 14.04 with all software updates on an HP laptop and have a Western Digital 500 GB auxiliary drive attached via USB. 
I get a message about a disk with UUID = (some large hex number) being not ready yet or not present when I boot.
I says I can wait, skip or manually recover. 
If I wait, everything seems fine.
How do I find out what disk is associated with the UUID displayed?

---

### Post by oldfred on 2015-10-12
Post these:
 sudo blkid -c /dev/null -o list
ls -l /dev/disk/by-id
cat /etc/fstab

Are you mounting a partition on USB drive in fstab? Boot is now so quick that USB drives may not be connected or up to speed to be correctly seen during boot. Is USB drive powered thru USB port or separate power connection?

---

### Post by cearlp on 2015-10-12
No USB device in stab, but the UUID in the message is for swap.

fstab shows the following:

/ was on /dev/sda5 during installation
UUID=09c4f318-..........  /  ext4   errors=remount -ro 0  1
swap was on /dev/sda6 during installation
UUID=e414a4b2-.........  none  swap  sw  0  0
swap was on /dev/sda8 during installation
UID=3ebc2e89-cf6a-49f6-9aa7-394657da1c3e  none  swap  sw  0  0   (**This is the UUID that appears in the not ready or not present message**)
/dev/disk/by-id/ata-HL-DT-ST_BDDVDRM_CT10L_K0591F63102  /mnt/ata-HL-DT-ST_BDDVDRM_CT10L_K0591F63102   auto nosed,nodev,nofail,x-gvfs-show  0  0

I am confused as to why there are two swaps. I guess this is the reason I get the message, but can I just delete it from fstab?

---

### Post by oldfred on 2015-10-12
How large are the swaps? I normally suggest 2GB unless very old system with less than 2GB of RAM.

And yes you can just delete either totally delete or change to a comment with # as first character.
I often get two swaps, but I have one on each drive and a new install adds them both. If you had a swap and did a auto install it probably added another, but if using Something Else is will find an existing swap and add that to fstab.

       sudo cp /etc/fstab /etc/fstab.backup
sudo nano /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

---

### Post by cearlp on 2015-10-13
Thanks oldfred, deleting it got rid of the message and the system boots normally.

---

