---
title: "fstab changes to mount and read/write usb connected HD"
date: 2014-06-19
forum: General Help
---

### Post by solotwit on 2014-06-19
Please help! I have Ubuntu 14.04 and am trying to change the fstab file to let me mount and read/write files to a 4tb WD Mybook formatted in NTFS. It is connected via usb 3.0 to my netgear 6250 router. I have tried many things but I keep getting an error saying "only root can mount...." I currently have this as my fstab 

//192.168.1.1/USB_Storage /media/public ntfs-3g guest 0 0

I have tried changing permissions by using nautilus but it still gives me that error. 
I made the directory media/public.
I have cifs-tools and util installed

Any ideas on how I should change that fstab line?

---

### Post by Bucky Ball on 2014-06-19
*Thread moved to **General Help**.*

This is a network drive (NAS)? If so, why are you trying to mount it (you have the IP address 192.168.1.1 at the start of your fstab line). If it is on the network you don't need to mount it. 

Open Nautilus and go to 'Network' or 'Network Connections' (I don't use Nautilus, but it's something like one of those). Is it there?

If this is not a network drive, diregard this post, except for the fact that if it is not a network drive then your fstab line is totally wrong. You don't need the IP. Just mount the drive with something like this:

```
#Entry for your USB drive:
UUID=6B8E2F2A62CEE191   /media/public     ntfs-3g defaults,locale=en_AU.UTF-8    $

```

... where the 'UUID=' should reflect the UUID of YOUR external USB. With it plugged in, run:

```

sudo blkid
```

Does it show up? If so, there you will see the UUID number of your external partitions. Replace the one in my example with yours. Good luck.

* Just to check it is there, present and correct, you can run:

[/code]
lusb[/code]

... in a terminal or open Gparted and have a look.

---

### Post by solotwit on 2014-06-19
Thanks for the quick response! In nautilus it show up under "browse network, windows network, WORKGROUP" but WORKGROUP asks for a password and doesn't seem to want to connect. If I run 
sudo blkid
I don't see it in there.Not in Gparted either. 
I'm not sure if this is a network drive or not. I'm just plugging an external hard drive into my wireless router.I spent some time trying to get a synology disk station to work last year and couldn't figure it out. 

Maybe my problem is different than I think, I would like to access this drive through my router and play movies and music from it with plex and do backups to it also. I thought getting it to mount would let me read/write to it, but maybe you can point me in a better direction?

---

### Post by Bucky Ball on 2014-06-19
If you're plugging it into the wireless router I guess it is a network drive but I suggest you find out for sure rather than waste your time. A regular external drive is not going to work the way you are planning to use it. If you plug it directly into the machine do you see it fine? And where did you get the IP you are using in your fstab line? Is that the IP of the router???

---

### Post by solotwit on 2014-06-19
I do see the drive if plugged into my laptop. The ip is the ip of the router. Why would the router have a usb for hooking up a external hd if it won't do anything? I'm looking at this article (one of many)
[http://askubuntu.com/questions/463956/mount-external-hard-drive-with-etc-fstab-on-ubuntu-14-04-problems](http://askubuntu.com/questions/463956/mount-external-hard-drive-with-etc-fstab-on-ubuntu-14-04-problems)

---

