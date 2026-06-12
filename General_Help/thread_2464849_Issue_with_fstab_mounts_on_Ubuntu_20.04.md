---
title: "Issue with fstab mounts on Ubuntu 20.04"
date: 2021-07-13
forum: General Help
---

### Post by plazman30 on 2021-07-13
I have 3 NFS mounts in my fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=b46bf4a6-474e-4640-8118-73417fc11582 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e033db47-ef4c-4623-9117-00f70d3b1ac4 none            swap    sw              0       0
#4 TB HD
UUID=85b5bef2-1ea8-4234-a5f1-a19bd6097c6a	/mnt/storage		btrfs	compress=lzo,noatime,autodefrag	0	0

#NAS Comics
nas.local:/volume1/comics /mnt/storage/comics nfs rsize=8192,wsize=8192,timeo=14,intr

#NAS Music Share
nas.local:/volume1/music /mnt/storage/music_library nfs rsize=8192,wsize=8192,timeo=14,intr

#NAS TV Show Share
nas.local:/volume1/tvshows /mnt/storage/tvshows nfs rsize=8192,wsize=8192,timeo=14,intr


```

Of the 3 NFS mounts, whichever is LAST in the fstab list will not mount on boot.

But if I run ```
sudo mount -a
```, it mounts without an issue. I've changed the order of all three, and whichever one is last on the list will not mount after I reboot the server, but will always mount with a ```
sudo mount -a
```

Any one have any ideas what's going on?

---

### Post by TheFu on 2021-07-14
Don't put *rsize=8192,wsize=8192,* options into the mounts. NFSv4 automatically negotiates the best values. Don't screw with those.  There are too many old, old, old, guides with those options that shouldn't have been included for about 15 yrs, since NFSv4 became the standard.

Is there a reason the NFS fstab entries don't include all the necessary fields?  The last 2 are missing.  They should be **0 0** according to the documentation.

I normally use these mount options for NFSv4 on the client-side:
```
nconnect=2,proto=tcp,intr,rw,async
```

As for mounts not mounting, I have 2 ideas.
[LIST]
[*]Always have a blank line at the end of every config file.  Some parsers don't know that EOF should be treated as EOL too. 1 extra blank line solves that issue.  My admin mentor taught me that in the 1990s.  Yes, it shouldn't matter. When it does, best to avoid it.

[*]When exports are from the same server, sometimes NFS needs a little help to understand them if they aren't different enough.  There's a numbering thing in NFSv4 - think of it as an identifier, not really a number. This helps the internals of NFS to not become confused.  It only needs to be added on the NFS server in the /etc/exports file. For example:

```
/d/D1/ebooks/Library    nextcloud(ro,async,root_squash[COLOR="#FF0000"],fsid=9[/COLOR]) 
```
Just ensure the fsid= has a unique number for each export. Nothing changes on the clients.
[/LIST]
I use read-only mounts for select, untrusted, systems. I don't trust nextcloud NOT to screw large data, but want to be able to view that data through nextcloud.  ;)

Anyways, give those a try.

---

### Post by plazman30 on 2021-07-14
I modified my /etc/fstab as follows:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=b46bf4a6-474e-4640-8118-73417fc11582 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=e033db47-ef4c-4623-9117-00f70d3b1ac4 none            swap    sw              0       0
#4 TB HD
UUID=85b5bef2-1ea8-4234-a5f1-a19bd6097c6a	/mnt/storage		btrfs	compress=lzo,noatime,autodefrag	0	0

#NAS Comics
nas.local:/volume1/comics /mnt/storage/comics nfs nconnect=2,proto=tcp,intr,rw,async 0 0

#NAS Music Share
nas.local:/volume1/music /mnt/storage/music_library nfs nconnect=2,proto=tcp,intr,rw,async 0 0

#NAS TV Show Share
nas.local:/volume1/tvshows /mnt/storage/tvshows nfs nconnect=2,proto=tcp,intr,rw,async 0 0

#Just a blank line
```

It still will not mount the last line. And if I move them about, the last line does not mount.

I have a synology NAS doing the export. It's GUI doesn't give me the option to set an ID.

---

### Post by TheFu on 2021-07-14
Between changes, are you forcing the file to be reparsed by systemd-mount?
Let's shake things up a bit. Changing it can ensure our changes are actually being picked up.

```
sudo mkdir /mnt/tv /mnt/comics /mnt/music
```
Then replace the NAS stuff in the fstab .... 
```
nas.local:/volume1/tvshows /mnt/tv     nfs proto=tcp,intr,rw,async 0 0
nas.local:/volume1/comics  /mnt/comics nfs proto=tcp,intr,rw,async 0 0
nas.local:/volume1/music   /mnt/music  nfs proto=tcp,intr,rw,async 0 0
```

```
sudo systemctl daemon-reload
sudo systemctl restart remote-fs.target
sudo mount -a
```

The daemon-reload regenerates the mount-unit files.  Each can be called separately afterwards.

If that doesn't work, seems the next step is to seek Synology help, since they may not be running a standard NFS server.

---

### Post by plazman30 on 2021-07-14
sudo mount -a has always worked without issue.

---

### Post by plazman30 on 2021-07-14
After I make the change, I am rebooting.  After reboot, only 2 of the 3 NAS shares mount. So, I do a sudo mount -a and then eveyrthing gets mounted.

---

### Post by TheFu on 2021-07-14
Did you try the suggested changes or not?

---

### Post by plazman30 on 2021-07-14
Not yet.  I will be doing so as soon as a I have a moment.

Need to make symlinks too, so apps don't break. I'll be doing it later this afternoon.

---

### Post by TheFu on 2021-07-14
By using nas.local, you are dependent on mdns running.  

I purge both avahi and mdns from my systems, perhaps using the IP address for the server instead would be helpful?   I have LAN DNS servers, so having multiple name resolution network services is confusing to me. It also means that the nsswitch.conf has to be managed on all the systems and each zeroconf device announces on the LAN "I'm here".  Then we need to have mdns watching for those, firewall rules to allow them passage, and , and, and, and ... it is a house of cards.

A NAS really should have a static IP. For anything that doesn't physically move, I set the static IP on-the-system, but for laptops or other difficult devices like network TV tuners, I can live using DHCP reservations to effectively provide static IPs for those few devices.

---

### Post by plazman30 on 2021-07-14
My NAS does have a static IP address.  I will try that too.

---

### Post by plazman30 on 2021-07-14
Ok, changing the fstab worked! I made symlinks back to the old locations. Now I just need to re configure some apps.

Thanks for the help!

---

### Post by TheFu on 2021-07-14
Stray character or something else?
If you'd like better performance, the nconnect=2 or nconnect=10 option, if supported by the NAS, can help.  Some background:
[https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.3-NFS-Changes](https://www.phoronix.com/scan.php?page=news_item&px=Linux-5.3-NFS-Changes) 
[https://patchwork.kernel.org/project/linux-nfs/cover/155917564898.3988.6096672032831115016.stgit@noble.brown/](https://patchwork.kernel.org/project/linux-nfs/cover/155917564898.3988.6096672032831115016.stgit@noble.brown/)
It is for kernels v5.3 and later.

---

