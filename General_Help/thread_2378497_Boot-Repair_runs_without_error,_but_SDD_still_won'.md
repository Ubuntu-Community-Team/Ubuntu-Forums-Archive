---
title: "Boot-Repair runs without error, but SDD still won't boot..."
date: 2017-11-23
forum: General Help
---

### Post by kalakuta72 on 2017-11-23
[FONT=arial]My xubuntu installation has stopped booting (I think after failing to complete a shutdown cycle properly), and I have tried several methods to repair it - e.g. using boot-repair and chroot plus grub-install (as per [these]("https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot") instructions).  No errors come up with either of these methods, but the hard drive is still not recognised as bootable (the BIOS sees an Ubuntu file system with the correct path to the shimx64.efi file but still no joy) Output of the boot-repair log here: [https://paste.ubuntu.com/26030606/](https://paste.ubuntu.com/26030606/). [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any advice gratefully received - I really don't want to have to perform a fresh install![/FONT]

---

### Post by Neill_R on 2017-11-23
Did you separate /  and /home into separate partitions. If so a fresh install might be the fastest. just install to a single partition and then move home to your old home partition. Note to others always have a list of the packages that have been installed.

---

### Post by oldfred on 2017-11-23
Boot-Repair must have seen some corruption somewhere as it tried to run fsck on all partitions, including flash drive's ext partitions.
One it said was ext3, but it converted it to ext2 because of errors in journal? Not sure how to recover from that.

I normally suggest full e2fsck on all ext family of partitions:
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, **change example shown** with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

Abnormal shutdown may cause file corruption if system is trying to do something.
      
 Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[https://en.wikipedia.org/wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

---

### Post by kalakuta72 on 2017-11-24
> **Neill_R said:**
> Did you separate /  and /home into separate partitions. If so a fresh install might be the fastest. just install to a single partition and then move home to your old home partition. Note to others always have a list of the packages that have been installed.

Thanks for the reply Neill.  Not sure I quite understand what I need to do - which is my home partition?  The one that isn't boot or swap?  So would I back up that partition and then copy it over to the new installation?  I feel I may be approaching (exceeding?) the limits of my linux 'expertise'...

---

### Post by oldfred on 2017-11-24
This shows all partitions:
sudo parted -l
And this will show what partitions you normally mount
cat /etc/fstab

Post this also:
df -h

---

### Post by kalakuta72 on 2017-11-25
sudo parted -l gives: [https://paste.ubuntu.com/26044312/](https://paste.ubuntu.com/26044312/)

cat /etc/fstab gives: [https://paste.ubuntu.com/26044342/](https://paste.ubuntu.com/26044342/)

df -h gives [https://paste.ubuntu.com/26044383/](https://paste.ubuntu.com/26044383/)

Thanks!

---

### Post by oldfred on 2017-11-25
You show an encrypted swap, which usually is from an encrypted /home.
So is system not booting because it cannot mount your encrypted /home?

I do not know encryption.

I had saved these, but now old, not sure if still relevant.
 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1](http://askubuntu.com/questions/719409/how-to-reinstall-grub-from-a-liveusb-if-the-partition-is-encrypted-and-there-i?rq=1)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

