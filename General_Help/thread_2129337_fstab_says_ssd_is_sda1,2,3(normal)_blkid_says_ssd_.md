---
title: "fstab says ssd is sda1,2,3(normal) blkid says ssd is sdb1,2,3(abnormal)"
date: 2013-03-25
forum: General Help
---

### Post by Singtoh on 2013-03-25
Hello all,

I just did a fresh install of ubuntu 12.10 64bit and noticed something strange. I have an ssd drive in the main bay of my laptop and a 1TB hdd in my ultrabay(thinkpad) During all previous installations of different flavors of ubuntu and others, my main drive(ssd) has always been sda1. During this installation the ssd is sdb1 and the 1TB is sda1. Further confusion is that Gnome-disk-utility sees the 1TB hdd as sda1 and the ssd as sdb1,sdb2,sdb3(never seen this before??) and "sudo blkid" gives me the 1TB as sda1 and the ssd with Ubuntu on it with partitions as sdb1 as /, sdb2 as /home and sdb3 as /swap. I am further confused that "fstab" says that sda1,sda2,sda3 is my ssd drive(as it should be and the uuid's matchup) but the "sudo blkid" produces the opposite sdb1,sdb2,sdb3 as my ssd(but the uuid's matchup) and the 1TB as sda1(uuid's matchup). This got me during the net install for when it said it would install grub, it installed grub to sda which is the 1TB storage hdd in the ultrabay. Other than this confusion the install went without a hitch. I have done this kind of install many many times and have never seen this happen before. Further, I noticed the same thing installing ubuntu 13.04 not using net install but using a live-cd. Something has changed and it's a bit confusing. I want to set my 1TB hdd with cfq scheduler and the ssd with noop or deadline as I always have in the past but now it's a bit mixed up?? Any suggestions how to fix this mess??

Cheers,

Singtoh

Singtoh

---

