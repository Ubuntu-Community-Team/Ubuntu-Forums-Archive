---
title: "[SOLVED] No space left on device -- NOT TRUE!"
date: 2008-06-23
forum: General Help
---

### Post by keystone on 2008-06-23
Hi, all.  I'm new to Linux and this forum, so forgive me if this has been asked and answered a lot.

I have Ubuntu 7.10 installed on two 300GB SATA disks using LVM.  (I haven't moved on to 8.04 because I haven't been able to get that CD to work -- perhaps a separate issue.)  I set up various partitions, including / at 10GB, /boot at 1GB, /usr at 10GB, swap space at 3GB or something, with about 275GB of the first disk and the entire second disk partitioned for use in LVM.  Got the system booted, set up the volume groups, logical volumes, everything I thought I was supposed to do.  I should now have an LVM partition of about 575 GB.

But when I try copying files either through Samba or directly in Linux, I get a "no space left on device" error, even though I have copied less than 9GB of data.

On advice from [[COLOR="Orange"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=833203"), I ran **df -h** to produce:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  8.8G     0 100% /
varrun                471M  172K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   84K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm
/dev/sda2             942M   35M  860M   4% /boot
/dev/sda5             9.2G  880M  7.9G  10% /usr
overflow              1.0M     0  1.0M   0% /tmp

```

(I don't know if /dev/sdb1 should be showing up here, but I did include it as part of my volume group, and it should be a full 300GB.)

So my question is, do I have an obvious problem?  Should I roll back to any point in the installation?  This wouldn't be a problem, as I have backups of all the data I've copied, and I haven't installed many apps.

Thanks for any help,
Keystone

---

### Post by HalPomeranz on 2008-06-24
It looks to me like the vast majority of your disk space isn't being mounted-- it's not showing up in the df output anyway.  You've filled up your root file system trying to copy data into a directory that you're apparently expecting to be the mount point for your extra disk space, but since the disk isn't mounted you're just writing it into the root file system.

You're going to need to add an entry to your /etc/fstab file to automatically mount the rest of your disk space.  It's difficult for me to advise you exactly what that entry should look like because I'm not sure how you've set up your LVM configuration.

---

### Post by kpkeerthi on 2008-06-24
> **keystone said:**
> 
But when I try copying files either through Samba or directly in Linux, I get a "no space left on device" error, even though I have copied less than 9GB of data.


Which partition did you copy the files to? /dev/sda1 ?

/dev/sda1 is 95% full. The rest 5% is reserved. More info [here]("http://wiki.archlinux.org/index.php/Ext3_Filesystem_Tips#Reclaim_Reserved_Filesystem_Space").
> **keystone said:**
> 
```

/dev/sda1             9.2G  8.8G     0 100% /

```


---

### Post by keystone on 2008-06-24
Thanks, Hal, thanks, kpkeerthi.  I copied files to /home/myname, which I had thought was mounted separately under /home, but I think Hal is right, that partition was never mounted.

I was sure I had mounted it, but it didn't show in /etc/fstab when I looked there just now.  So I mounted it again, in the same way I thought I originally had (**sudo mount /dev/home_vg/home_lv /home**, where **home_vg** and **home_lv** are a volume group and a logical volume I had created through LVM).

Now **df -h** shows me:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  8.8G     0 100% /
varrun                471M  172K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   84K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm
/dev/sda2             942M   35M  860M   4% /boot
/dev/sda5             9.2G  880M  7.9G  10% /usr
overflow              1.0M     0  1.0M   0% /tmp
/dev/mapper/home_vg-home_lv
                      563G  198M  534G   1% /home

```

And that's what I want.  I suppose I'll just have to clean out / and re-copy my files, since there's no way I have 8.8G of data there -- it must be just a hangover from /home being part of that partition.

So I guess my new question is: Is this a known bug in LVM2?  I'm pretty sure this is exactly what I had done previously, but it didn't work out as I expected.  I can't find any reports of this being an issue, so I think maybe I just screwed it up the first time.

Thanks to both of you for helping me understand some diagnostic tools.

---

### Post by HalPomeranz on 2008-06-24
> **keystone said:**
> I suppose I'll just have to clean out / and re-copy my files, since there's no way I have 8.8G of data there -- it must be just a hangover from /home being part of that partition.


What I suggest is that you temporarily unmount /home and then remount the /dev/mapper/home_vg-home_lv file system someplace like /mnt.  Then you can move all the files you mistakenly copied into /home/myname when the LVM2 file system wasn't mounted:

```

sudo umount /home
sudo mount /dev/mapper/home_vg-home_lv /mnt
sudo mv /home/myname /mnt
sudo umount /mnt
sudo mount /dev/mapper/home_vg-home_lv /home

```

That will save you having to re-transfer the data you already copied to the system.

---

### Post by keystone on 2008-06-24
Oops!  Too late, I already mounted /home.  It's really not a big deal, though, I just have to click-and-drag from one Windows folder to one directory in Samba.

When I mounted it, the files in /home/myname disappeared, yet according to **df** I still have that 8.8G of data sitting in / .  I can't even find it to delete it, since the files are gone.  **df -h** shows 8.8G of used space on /, but **du / -hc** gives me a sum of 978M, which seems more reasonable for the root partition.

So it seems like **df** is still showing that space as allocated, even though the files aren't listed.  Is there a way to de-allocate the space?

---

### Post by russlar on 2008-06-24
related to the /home not being mounted: check /etc/fstab and make sure that there's an entry in there for /dev/mapper/home_vg-home_lv

---

### Post by danwood76 on 2008-06-24
You need to unmount your /home and the files you copied will re appear.
Then you can delete them and remount your /home

---

### Post by keystone on 2008-06-24
> **russlar said:**
> check /etc/fstab and make sure that there's an entry in there for /dev/mapper/home_vg-home_lv

There is not an entry there, even though I ran **sudo mount /dev/home_vg/home_lv /home** and **df** shows that /home is mounted.  Should I add that line manually, even though this volume is supposedly being managed by LVM?  And would the following be an appropriate addition to fstab?
```

/dev/mapper/home_vg-home_lv    /home    ext3    defaults    0    0
```
Just guessing at this line by following the model from some other lines.

---

### Post by keystone on 2008-06-24
> **danwood76 said:**
> You need to unmount your /home and the files you copied will re appear.

My understanding grows.  Thanks, I'll do this and run Hal's sample code above where he was writing about unmounting.

---

### Post by keystone on 2008-06-24
OK, great.  Following HalPomeranz' and danwood's advice, **df** now looks like I think it should:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  379M  8.4G   5% /
varrun                471M  172K  471M   1% /var/run
varlock               471M     0  471M   0% /var/lock
udev                  471M   84K  471M   1% /dev
devshm                471M     0  471M   0% /dev/shm
/dev/sda2             942M   35M  860M   4% /boot
/dev/sda5             9.2G  880M  7.9G  10% /usr
overflow              1.0M     0  1.0M   0% /tmp
/dev/mapper/home_vg-home_lv
                      563G  8.5G  525G   2% /home
```

I think my last remaining issue is to confirm that this mounting should be listed in fstab as I wrote above.  Is that correct?

---

### Post by keystone on 2008-06-24
Thanks to everyone!  You were all very helpful.

---

