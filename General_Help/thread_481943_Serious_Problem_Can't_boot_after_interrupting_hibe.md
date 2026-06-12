---
title: "Serious Problem: Can't boot after interrupting hibernate resume"
date: 2007-06-23
forum: General Help
---

### Post by zakaria.cse on 2007-06-23
Hi,
I have been using Ubuntu since last 3 months. Everything was fine. But yesterday I made a problem.

Yesterday to shutdown I used hibernate option. After turn on, it seemed to late to resume computer. So I restarted it by pressing the reset button. Suspending the hibernate process caused a serious problem in booting Ubuntu. Now it can't load gui. While booting it shows lots of error messages like followings:

```

[  25.134564] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[  25.245677] ata1.00: (BMDMA stat 0x25)
[  25.345678] ata1.00: cmd 25/00:08:0a:70:51/00:00:12:00:00/e0 tag 0 cdb 0x0 data 4096 in 
[  25.456768] ata1.00: EXT3-fs error (device sda3):  ext3_get_inode_loc: unable to read inode block - inode=834427, block=1671184

......

.11 can't open /lib/init/vars.sh
chmod: changing permission of '/var/run/screen': Read-only file system
chmod: changing ownership of '/tmp/.X11-unix': Read-only file system

......

* Starting GNOME Display Manager        [fail]


```

After showing the messages like above more that 100 times ubuntu starts (it takes 10 minutes) into command mode (no gui). 

```

Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/a55263b8-9bf8-4032-b8a8-41e2cb0e01e5) = sda8(8, 8)
kinit: trying to resume from /dev/disk/by-uuid/a55263b8-9bf8-4032-b8a8-41e2cb0e01e5
kinit: No resume image, doing normal boot...

Ubuntu 7.04 (none) tty1

(none) login:


```

After login I can view my files by ls commad but cannot create any file/directory. It gives following message:
```

zakaria@(none):~$ mkdir test
mkdir: cannot create directory 'test': Read-only file system

```


Please help me to recover my Ubuntu.
Zakaria

---

### Post by zakaria.cse on 2007-06-23
Now I have another problem - I can't boot in my windows partition. May be my SATA hard disk is gone. I tried to check ubuntu partition from live CD by typing following command:
```
sudo fsck /dev/sda3
```

It gives me following type messages:

```

Pass 1: Checking inodes, blocks, and sizes
Error reading block 360450 (Attempt to read block from filesystem resulted in short read) while doing inode scan. Ignore error<y>? yes

Force rewrite<y>? yes

```


I tried to copy data on ntfs partitions by connecting this hard disk to my another computer. But the drives are not accessible. When I click to open a drive it ask me to format. I can't understand how hibernate on ubuntu effects on my windows partition.

Can anyone tell me how can I fix my hard disk? Seems all my data are lost :(
Please reply.

---

### Post by mikealive on 2007-06-23
i have a problem similar to yours, and it seems that nobody can help me.

[http://ubuntuforums.org/showthread.php?t=479545](http://ubuntuforums.org/showthread.php?t=479545)

---

### Post by mikealive on 2007-06-23
anyone?

---

