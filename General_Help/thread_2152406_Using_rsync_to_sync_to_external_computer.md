---
title: "Using rsync to sync to external computer"
date: 2013-06-07
forum: General Help
---

### Post by rmcellig on 2013-06-07
This is what I am using to currently sync my lps folder from my Records partition to an external usb drive attached to my computer. Works great. 

rsync -r -t -p -o -g -v --progress --delete -s /media/records/lps/ /media/music/lps

What I would like to do is sync my lps folder from my Records partition to an external usb drive hanging off my other linux computer. How can I modify the code above to do this?

---

### Post by Rebelli0us on 2013-06-07
First mount the network share in file manger, then the rync destination will be something like    ~/.gvfs/share__name

Look in your home folder under ~/.gvfs  ... in some distros it's under  /usr/local/share  but just look for **.gvfs**

---

### Post by Rebelli0us on 2013-06-07
BTW, I think gvfs stands for "gnome virtual file system"

---

### Post by oldfred on 2013-06-07
I used Samba when my laptop was Windows, but literally got so frustrated with just about any update in Windows on the laptop forcing a reconfigure, I installed Ubuntu on laptop and then started using NFS. After I posted that a couple of times, someone with more knowledge suggested I use SSH.

[https://help.ubuntu.com/12.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/12.04/serverguide/C/openssh-server.html)
In the menu go accessories > terminal and copy and paste
sudo apt-get install openssh-server openssh-client
Do this on both machines.

But I used NFS and at first it seemed difficult to set up. But once configured I could just run a script to mount partitions & another to rsync folders.

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)
[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

Scripts I run with new install of Ubuntu to install & configure NFS (inside script so sudo implied)
```

#NFS setup
fname_exp=/etc/exports
nfs1="/mnt/data 192.168.1.0/24(rw,no_root_squash,async)"
nfs2="/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)"
echo $nfs1 >> $fname_exp
echo $nfs2 >> $fname_exp


# For NFS /etc/exports already edited rpcbind replaced portmap 12.04
apt-get install nfs-kernel-server nfs-common rpcbind
dpkg-reconfigure rpcbind
exportfs -a
# still portmap?
service portmap restart


```

Script to Mount my Laptop folders in my Desktop 
```
#!/bin/bash
# check that exports has been updated and path is correct
#/etc/exports
#/mnt/data 192.168.1.0/24(rw,no_root_squash,async)
#/mnt/shared    192.168.1.0/24(rw,no_root_squash,async)

mkdir /mnt/data_LT
mkdir /mnt/shared_LT
mount 192.168.1.100:/mnt/data /mnt/data_LT
mount 192.168.1.100:/mnt/shared /mnt/shared_LT

```
Script to rsync
```
#!/bin/bash
# run Mount_NFS.sh first
# a - archive, retain file settings
# r - recursive / subdirectories
# u - update, only newer
# v - verbose
# P - keep partial files and report progress
# need to exclude cache from mozilla or houseclean first.
echo "starting..."

rsync -aruvP /mnt/data_LT/Documents /mnt/data
rsync -aruvP /mnt/data_LT/Projects //mnt/data
rsync -aruvP /mnt/data_LT/PDF /mnt/data

```

---

### Post by rmcellig on 2013-06-07
Oldfred,

This is great information. I have never done anything like this before. Maybe it's about time I take the plunge and look into setting up an NFS server. I will carefully look at the links you mentioned in your post. Thanks!!

---

### Post by rmcellig on 2013-06-07
These are the machines I use in my home LAN

HP DV6 laptop (Linux Lite 1.0.6 beta)
HP DV2000 laptop (Linux Lite 1.0.6 beta)
Dell 3000 Desktop (Linux Lite 1.0.4)
iMac 24" circa 2006 (OS X Snow Leopard)
Mac G4 mirror circa early 2003 or 2004 OS X Snow Leopard)

I use my iMac and Dell 3000 to record my weekly radio show from an AIWA -945 circa 1980. I use an arecord script on the Dell to record my shows. Works great. I am also in the middle of digitizing all of my LP's (around 6000), using my Dell 3000 and Audacity to save the files as FLAC files. I then copy them over to my DV6 through Samba. I use rsync ( in my initial post), to back up to an external USB drive. Crashplan is used to back up the FLAC files to the cloud.

It would be really great if I could simplify the current way I am doing things so that the workflow is more efficient and makes more sense. I spend about 80% of my computer time in Linux these days, and am still learning things. :)

---

### Post by oldfred on 2013-06-07
I do not know about Macs and what details may be different.

I also ripped to flac all my CD with Sound converter/Sound juicer several Ubuntu versions ago, but only have about 10 CDs. :) All that you have will be a huge task.

I started to learn a bit about bash just by listing my history with the history command and copying those commands into a bash script.

 Ripping Music Issues
[http://ubuntuforums.org/showthread.php?t=1518919](http://ubuntuforums.org/showthread.php?t=1518919)
Python music software:
[http://wiki.python.org/moin/PythonInMusic](http://wiki.python.org/moin/PythonInMusic)

---

### Post by rmcellig on 2013-06-07
This link is so easy to follow when setting up an NFS server/client. Thanks for providing this. When I have some time I will try this on my two laptops and see what happens.

[http://mostlylinux.wordpress.com/network/nfshowto/#createtheshare](http://mostlylinux.wordpress.com/network/nfshowto/#createtheshare)

I don't think I will live long enough to digitize all of my LP's but I tell you it sure is keeping me busy. :)

---

