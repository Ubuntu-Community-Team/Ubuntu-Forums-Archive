---
title: "Error writing/deleting &lt;foo&gt; Read-only file system"
date: 2019-04-28
forum: General Help
---

### Post by ubuntini2 on 2019-04-28
Have a frustrating problem with either deleting or simply updating files on my dual boot ubuntu-windows setup.


I am stuck in a logged-out loop (Ubuntu) which I believe is due to a full root partition.
See attached)


So I am in the process of simply trying to delete files from the cmd line.
However whenever I do so, even when using sudo, I get a 'Read-only file system'


Ditto for updating files.
ie from the root shell I do
sudo nano /etc/default/grub


make some edits, do a Ctrl-X and try to save.
Get same error
"Error writing.<foo> Read-only file system"


Can anyone tell me what is going on?

[ATTACH=CONFIG]283128[/ATTACH][ATTACH=CONFIG]283129[/ATTACH]

---

### Post by Impavidus on 2019-04-29
When you boot in recovery mode, the root filesystem gets mounted read-only. You have to remount it read-write before you can save any files:```
mount -o remount,rw /
```

You have collected quite a lot of stuff to fill up a 40GB root partition, considering that you have a separate /home partition. Do you know how to investigate if anything peculiar is going on? Like overflowing log files or files supposedly written to another partition, with that partition curently unmounted.

---

### Post by ubuntini2 on 2019-04-29
Thanks.
The first thing I am going to do once I am able to boot into my desktop is look into how to prevent this from happening again.
Guessing it could be a combination or orphaned packages, and overflowing log files.

---

### Post by Impavidus on 2019-04-29
This guide is a few years old, but still accurate. Command line stuff rarely changes anyway: [https://ubuntuforums.org/showthread.php?t=1122670](https://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by ubuntini2 on 2019-04-29
Thanks!

---

