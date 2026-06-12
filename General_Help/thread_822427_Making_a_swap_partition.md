---
title: "Making a swap partition"
date: 2008-06-08
forum: General Help
---

### Post by Silpheed2K on 2008-06-08
I dont have one but I want one... since my system would have no other option but to crash after it's RAM gets full but I doubt that will ever happen or much at least. (2GB RAM but the major RAM consuming happens in Windows)
So how do I set up a swap partition for my GNU Linux?
I have 1GB of unformatted space and I'm having a hard time knowing which guide I should follow.
Thanks to anyone that helps.

---

### Post by Kinnza on 2008-06-08
im pretty sure that if you have 2g ram you need at least 2g swap partition

i can tell ya how to create the partition - use gparted 
but i dont really know how to make ubuntu use it as swap after you installed it (i did that before installation)

---

### Post by geirha on 2008-06-08
1GiB is a nice size, but I'd recommend, as Kinnza does too, at least the same ammount as your physical memory.

Boot up your ubuntu CD, it has gparted installed in the live-session. Use it to add a swap partition. When it's added, boot back to your normal system and run ```
sudo blkid
``` in a terminal. Identify your new swap partition in the output of that command, it should have an UUID="....".

Edit /etc/fstab (**gksu gedit /etc/fstab**) and add a line like this:
```
UUID=1234abcd-.... none swap sw 0 0
```
(replacing 1234abcd-.... with the correct UUID of course)
Then run ```
sudo swapon -a
free
``` The first command will mount all swap partitions listed in /etc/fstab, the second command should list the current memory usage (and how much swap is available)

---

### Post by Silpheed2K on 2008-06-08
I did what you said except i had to change the fstab entry a little bit... when I go to swapon it says i gave it an invalid argument even though it sees the swap and automatically puts its information in.
any suggestion? and my swap is appearing in the places menu and when i click it, it says i dont have permission to mount.

edit: oh yeah
```
rex@rex-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       2073892     673852    1400040          0      32552     351500
-/+ buffers/cache:     289800    1784092
Swap:            0          0          0
```

---

### Post by geirha on 2008-06-08
It sounds like you've made an ext3 partition instead of a swap partition (a swap partition should not appear in the places menu). When you create the partition, you need to set "Filesystem" to "linux-swap" (I should've mentioned this earlier, but I forgot). If you boot back into the liveCD and run gparted again, you should be able to right click the partition you created earlier and select "Format to"->"linux-swap". This will give it a new blkid, so you'll need to edit /etc/fstab again.

---

### Post by VMC on 2008-06-08
Here is a good document to explain Swap. You can choose either Swap Partition or Swap File
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by Silpheed2K on 2008-06-08
> **geirha said:**
> It sounds like you've made an ext3 partition instead of a swap partition (a swap partition should not appear in the places menu). When you create the partition, you need to set "Filesystem" to "linux-swap" (I should've mentioned this earlier, but I forgot). If you boot back into the liveCD and run gparted again, you should be able to right click the partition you created earlier and select "Format to"->"linux-swap". This will give it a new blkid, so you'll need to edit /etc/fstab again.

thanks after i made that change and edited again it worked.. and i changed the fstab entry to

```
UUID=12213d25-ce33-4b16-9bdb-b6dbb142294e       swap    swap    sw  0  0
```
i know /dev/sda2 could've been in the UUID places part i was just wondering why you do it by UUID instead but i guess that can be answered later.
It works now and thanks for your help.

---

### Post by geirha on 2008-06-08
> **Silpheed2K said:**
> thanks after i made that change and edited again it worked.. and i changed the fstab entry to

```
UUID=12213d25-ce33-4b16-9bdb-b6dbb142294e       swap    swap    sw  0  0
```
i know /dev/sda2 could've been in the UUID places part i was just wondering why you do it by UUID instead but i guess that can be answered later.
It works now and thanks for your help.

It saves you some hassle later on. If you add a new hard drive for instance, /dev/sda may suddenly be called /dev/sdb. Then all entries like /dev/sda1 and /dev/sda2 must be changed to /dev/sdb1 and /dev/sdb2 in /etc/fstab. Their UUID will stay the same, so if you use the UUID instead of the device nodes, you don't need to change anything, it will just work as if nothing happened.

---

