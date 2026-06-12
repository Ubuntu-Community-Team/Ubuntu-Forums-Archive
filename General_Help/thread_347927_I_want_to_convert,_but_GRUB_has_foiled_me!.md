---
title: "I want to convert, but GRUB has foiled me!"
date: 2007-01-28
forum: General Help
---

### Post by pcaulfie on 2007-01-28
Total newbie here, but I have spent the last few days configuring the latest Ubuntu Edgy.

I was in the process of mounting my network drives and on reboot, when Grub is supposed to do its thing I get : 'GRUB _' <--- with the blinking cursor.

I loaded up LiveCD and went in a restored my original /etc/fstab file to remove the automatic mounting of the network drives.

So what the heck happened to Grub?  I tried to reinstall, but I get an error, something about bad blocks.  I don't remember the exact error, I had to go boot into XP because I couldn't see the "Post New Thread" button in Mozilla on the LiveCD to write this.

```
sudo fdisk -l
sudo mkdir /mnt/root
sudo mount /dev/sda2 /mnt/root  #sda2 is my Linux partition, sda1 is XP
sudo chroot /mnt/root su
sudo grub-update  #it didn't recognize this command
```

Then I tried
```
sudo grub-install /dev/sda2  #got the bad block error...
```  

If it helps, I boot grub with a modified windows bootloader so GRUB must not be on the MBR of sda.  I don't really know where GRUB is installed...maybe finding that out would help?  I thought it was supposed to be on /dev/sda2.

I am really liking Ubuntu, but really don't want to reinstall because of all the configuring I've already completed.

Any thoughts?

---

### Post by housam on 2007-01-28
Try to use the [super grub. disk ]("http://supergrub.forjamari.linex.org/"), it may help fix it.

---

### Post by pcaulfie on 2007-01-28
Housam, thanks for the tip.

i was able to restore Grub to the original partition and it worked.  Thank you VERY much!  I'm sure Supergrub will come in handy many times to come.

---

