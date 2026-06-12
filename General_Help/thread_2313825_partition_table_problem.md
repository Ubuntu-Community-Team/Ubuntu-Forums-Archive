---
title: "partition table problem"
date: 2016-02-16
forum: General Help
---

### Post by Dan Z on 2016-02-16
Running UBUNTU 14.04,only OS on hard drive.

Today while using Clonzilla to create an image of /sda, my UPS burped and the PC lost power. The PC recovered ok, but when I tried to start another image job I got an error in Clonzilla:

"unknown partition table format on disk /dev/sda", then Clonzila terminated. 

I also noticed that on boot-up, now I get the GRUB screen. I don't think I used to get that, but I could be wrong, as I let the machine run many days without re-booting and just may not have noticed. 

Otherwise the machine seems to be working fine.

I see I can use Gparted to fix the partition table, but don't wan't to make matters worse. 

Or will a restore from backup do it?

Thanks for any advice DAN

---

### Post by grahammechanical on 2016-02-16
> I see I can use Gparted to fix the partition table, but don't wan't to make matters worse. 

I say that you will make things worse because there is not a problem with the partition table otherwise you would not be able to load Ubuntu. The problem is with Clonezila. Which I know nothing about.

Regards.

---

### Post by Dan Z on 2016-02-16
OK,Thanks, I have also posted the issue to Clonzilla forum.
 
BUT -
I wonder why the GRUB screen comes up, instead of going direct to Ubuntu on boot up.
Another PC I have with only Ubuntu on it goes direct to Ubuntu on boot up.

Thanks DAN

---

### Post by oldfred on 2016-02-16
After abnormal shutdown, grub knows it did not shutdown normally and presents menu so you can possibly boot in recovery mode and make repairs.

If systems if doing something during an abnormal shutdown, fsck is often required.
       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

