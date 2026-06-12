---
title: "Mounting Help"
date: 2014-08-16
forum: General Help
---

### Post by gio4 on 2014-08-16
So I ran into a bit of a problem.  I was messing around with UFW and I locked myself out of my server.  I am guessing I forgot to open the port I am using for SSH.

So here is what I decided to do, I booted up the server in Rescue Mode, and now I am trying to mount my hardrives/raids (Not very experienced at using Linux so I don't know the difference)

So now that I am doing that, I ran into another problem.

So this is what I am doing.

mount /dev/sda2 /mnt
mount /dev/sdb2 /mnt
mount /dev/sda3 /mnt
mount /dev/sdb3 /mnt

I tried doing that and every time I get this message mount: unknown filesystem tyep 'linux_raid_member'

I've been looking around all over the internet trying to find a fix but I haven't been able too.

Another thing I though about is reinstalling the OS but I believe it formats all the data, which is something I don't want.

Hopefully someone can help me find a fix :)

Thanks!

---

### Post by steeldriver on 2014-08-16
If you're using RAID, then you need to mount the array, rather than trying to mount the individual block devices that make up the array

I suggest you start by identifying the devices and filesystems using one of

```

parted -l

blkid -c /dev/null

fdisk -l

```

(fdisk is a last resort as it doesn't really understand RAID or GPT disks) - you want to be looking for something like /dev/md0 or /dev/mapper/xxx

---

### Post by gio4 on 2014-08-16
I found all the devices and filesystems but when I do the command to mount them, I get this message 

[COLOR=#000000]mount: unknown filesystem tyep 'linux_raid_member'

Any ideas?[/COLOR]

---

### Post by steeldriver on 2014-08-16
What exact mount command are you giving? what is the output of

```

sudo mdadm --examine --scan

```

---

### Post by gio4 on 2014-08-16
I got this:

root@rescue:~# sudo mdadm --examine --scan
ARRAY /dev/md2 UUID=40dbfa1d:0564e71f:a4d2adc2:26fd5302
ARRAY /dev/md3 UUID=3fc65b6f:27220b61:a4d2adc2:26fd5302

---

### Post by steeldriver on 2014-08-16
OK so you would do something like

```

mkdir /mnt/md{2,3}

mount /dev/md2 /mnt/md2
mount /dev/md3 /mnt/md3

```

If 'mount' is unable to figure out the filesystem type, you may need to add it explicitly e.g. -t ext4

BTW why are you doing this exactly? it should only be necessary to have / (and /etc, if on a separate partition) mounted in order to run ufw to re-open your SSH port - and they should be mounted already if you are in recovery mode. The most you would usually need to do is re-mount / in RW mode.

---

