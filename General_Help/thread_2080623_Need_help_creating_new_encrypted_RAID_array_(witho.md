---
title: "Need help creating new encrypted RAID array (without reinstall)"
date: 2012-11-04
forum: General Help
---

### Post by vcrpcant on 2012-11-04
I'm on Ubuntu 10.04 desktop system

I'd like to add two more hard drives with 3TB and mount them as an encrypted RAID 1 array (LUKS)
(I already know how to use parted to do this right)

How do I do that?

I don't want to reinstall my system

I've found several guides that are old :(

It should mount automatically at boot

I would like to do all of this at the terminal

---

### Post by vcrpcant on 2012-11-05
bump

---

### Post by vcrpcant on 2012-11-05
Well, I've managed to get this done.

It seems to be working. 
I rebooted several times and everything seems ok.
Only one issue: I'm always asked to enter the LUKS password twice for this new raid array, but after googling it seems to be a bug.

**Can somebody please take a look and tell me if I missed something ou make some suggestions?** :)

sudo mdadm --create --verbose /dev/md4 --level=raid1 --raid-devices=2 /dev/sde1 /dev/sdf1
sudo mdadm --detail /dev/md4
sudo cryptsetup luksFormat /dev/md4
Set up the device mapper:
sudo cryptsetup luksOpen /dev/md4 3TBraid
Confirm it worked:
sudo cryptsetup status 3TBraid
sudo mkfs.ext3 /dev/mapper/3TBraid
sudo mdadm --detail --scan
and paste the new array info in /etc/mdadm/mdadm.conf
sudo cryptsetup luksUUID /dev/md4
7df706aa-2daa-2612-bcdd-c67a716db62a
add this to /etc/crypttab:
3TBraid UUID=7df706aa-2daa-2612-bcdd-c67a716db62a none luks
sudo blkid
/dev/mapper/3TBraid: UUID="6fc6661a-218f-29ab-9f81-9bf7a7e96877" TYPE="ext3"
add this line to /etc/fstab:
UUID="6fc6661a-218f-29ab-9f81-9bf7a7e96877" /mydata ext3 defaults 0 2

---

