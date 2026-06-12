---
title: "GRUB upsate interrupted"
date: 2013-12-03
forum: General Help
---

### Post by zankaa222mobile on 2013-12-03
So basically, I was updating GRUB from my wubi install of Ubuntu because the one on my dedicated partition wouldn't work. My power turned off during the update. I am now stuck with a computer that refuses to boot and no way of installing grub to a disc to boot my PC. Can anyone help?

---

### Post by oldfred on 2013-12-03
Wubi boots from Windows and is just a file inside the Windows NTFS partition. If power failed while writing inside a NTFS partition you may have corrupted the NTFS partition and/ or the pseudo partition as a Linux formatted file inside the NTFS partition.

You may need to run chkdsk first from Windows or your Windows repairCd or flash drive.

Then you need an Ubuntu liveCD or flash drive.
 [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
Then check if you can mount it & read it:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

---

