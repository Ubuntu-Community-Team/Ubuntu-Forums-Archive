---
title: "mdadm RAID 0 setup"
date: 2016-03-22
forum: General Help
---

### Post by jaw1959 on 2016-03-22
So I'm trying to make a 2 disk RAID 0 array on my home server (I'm not interested in a debate about the pros and cons of a raid 0 array; this is just for temporary storage until I can make a raid 10 array on another machine, and i need raid 0 to get the size I need out of the disks I have, the data is only media anyway, so if it's lost, it's not the end of the world). I've done this in the past, and it worked well. I can't seem to make it work any more. I've found some online tutorials, and worked from them, but my issue seems to come after a reboot. Here's a brief summary of the steps I've taken:

[LIST=1]
[*]partition the drives, and leave them unformatted
[*]install mdadm
[*]create the array (sudo mdadm --create /dev/md0 --chunk=256 --level=0 --raid-devices=2 /dev/sd[ab]1 --verbose)
[*]get info on the resulting array (sudo mdadm --detail --scan --verbose)
[*]copy the output to /etc/mdadm/mdadm.conf (the output is: ARRAY /dev/md0 level=raid0 num-devices=2 metadata=1.2 name=workbuntu:0 UUID=18b9753c:23a3bb06:71a7f3cc:37bd4ba5 devices=/dev/sdb1,/dev/sdc1)
[*]create the folder I will eventually map to the array (/store)
[*]create the file system on the array (sudo mkfs.xfs /dev/md0)
[*]edit fstab to mount the array at the folder I created (the line in fstab for this reads: /dev/md0 /store xfs defaults 0 0)
[*]run sudo mount -a to test if my fstab line works (and it does)
[*]set permissions on the folder with chmod 755 /store
[*]then just for another test, I created a folder, containing a text file, and copy it to the new array (which seems to work).
[*]from here, I reboot, and this is where things go wrong. The system shuts down, and then it hangs on startup, eventually dumping me to a recovery mode that gives me a limited CLI. from here, I use vim to edit the fstab file, comment out the line I created at step 8, save/close the file, and restart.
[*]once things come back up, I run sudo mdadm --detail --scan --verbose again, and to my surprise, the result is different than it was previously in step 5, and it now reads: (ARRAY /dev/md/workbuntu:0 level=raid0 num-devices=2 metadata=1.2 name=workbuntu:0 UUID=18b9753c:23a3bb06:71a7f3cc:37bd4ba5 devices=/dev/sdb1,/dev/sdc1) - note that what used to say "/dev/md0" now says "/dev/md/workbuntu:0" (workbuntu is what I named the virtualbox install I'm working from, I've seen similar behavior on my physical machine where I saw the same issue last night).
[/LIST]

So that's what I've done so far. Form the info I've seen, I believe I'm following all of the necessary steps, it's just that I'm getting unexpected results.

This is the site I've been working from. [http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/](http://www.howtogeek.com/51873/how-to-setup-software-raid-for-a-simple-file-server-on-ubuntu/)

Can anyone spot where I'm going wrong with this?

---

### Post by NeooeN on 2016-03-23
Just guessing: what about mounting not by path to block device but by UUID?```
UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /whatever xfs defaults 0 0
```

---

### Post by Nuno_Abreu on 2016-03-24
I think I know the answer because I've ran into problems with the mdadm configuration file. Let's see if it works.
Please edit the configuration file:
```
sudo nano /etc/mdadm/mdadm.conf
```


There should be an uncommented line specifying your ARRAY, but instead of matching md0, it should be workubuntu:0. So, the line should be something like this (paste it if it works):
```
ARRAY /dev/md0 level=raid0 num-devices=2 UUID=[COLOR=#000000]18b9753c:23a3bb06:71a7f3cc:37bd4ba5
```
[/COLOR]

---

