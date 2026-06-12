---
title: "EXT4/fd (sda1): previous I/O error to superblock detected during boot"
date: 2013-03-05
forum: General Help
---

### Post by thom_ on 2013-03-05
Hello, I am using Ubuntu 11.10 32 bit. Yesterday, my computer had some line error during boot-time, showed EXT4/fd (sda1): previous I/O error to superblock detected (screenshoot : [http://i.imgur.com/TMow5UU.jpg]("http://i.imgur.com/TMow5UU.jpg")). On this condition, my compie still could reached Desktop, but then, my Desktop showed a dialog window with unreadable-character, (screenshot : [http://i.imgur.com/YmljPwk.jpg]("http://i.imgur.com/YmljPwk.jpg")). After that, it wouldn't show the Unity and some shortcut folders on Desktop became unknown-file-like (screenshot : [http://i.imgur.com/OJJZvC2.jpg]("http://i.imgur.com/OJJZvC2.jpg")).

Could any body tell me what is this and how could I get rid of it?

---

### Post by oldfred on 2013-03-05
I might first try fsck to see if that repairs issues with partition.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

---

