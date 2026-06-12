---
title: "sharing files on dual-booted system"
date: 2018-01-21
forum: General Help
---

### Post by rolfUser on 2018-01-21
The Internet connection on Ubuntu 17.10 stopped working. The icon on the upper-right hand side of the screen says it is connected but doesn't actually connect. Updates would not load up and now I am just stuck with the Windows 10 partition.

Now When I start up Ubuntu, the screen shows up like this. At other times, it did load up properly, but this time, I am stuck with a screen like this:

[ATTACH=CONFIG]278281[/ATTACH]
[ATTACH=CONFIG]278280[/ATTACH]

I don't know if I can recover Ubuntu to be working optimally again. I think it is best to delete the OS altogether and then reinstall.
The first step for me would be to** recover the files I saved by accessing them from Windows and then back them up on a USB drive.**

Some tutorials explain how it is done, but you need to be able to access Linux in order to make it work.
[https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/](https://www.howtogeek.com/176471/how-to-share-files-between-windows-and-linux/)

I have tried **Ext2Fsd**, but it does not want to load up.
Are there any known methods to share Ubuntu files from Windows 10 without having to do something on Linux?

---

### Post by oldfred on 2018-01-21
If corruption issues on a Linux partition, Windows tools will not work.

 Must be unmounted:
Try "e2fsck -f /dev/sda5". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean. 

   To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sda5 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda5
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sda5

---

