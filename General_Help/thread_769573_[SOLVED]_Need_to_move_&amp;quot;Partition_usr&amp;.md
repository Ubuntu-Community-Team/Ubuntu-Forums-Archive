---
title: "[SOLVED] Need to move &amp;quot;Partition: /usr&amp;quot; contents if possible."
date: 2008-04-26
forum: General Help
---

### Post by Bruce M. on 2008-04-26
Xubuntu 7.10 but I'm sure that that doesn't matter.

I re-installed Xubuntu yesterday and with different partitions. I found that I had a lot of wasted space in my home partition as I use my second HD for stuff I create/save like documents, images pdf files etc.

So yesterday with the Alt CD I reinstalled Xfce creating:

10.00G = fat32 - dos (now deleted)
65.21G = Extended Partition with the following Logical Partitions
  10.0G = / - shows as: 9.31G = "BOOT"
  30.0G = /home - shows as: 27.94G
  28.5G = /usr - shows as: 26.53
  01.5G = swap - shows as: 1.43G

Thinking that /usr was a partition for a "user" I quickly learned that it is the /usr folder from the root partition

So here's the questions;

Can I "move" the contents of that partition to the root partition and recover that partition for myself?

 or

Do I have to re-install at least the root and recover that partition through the Partition Editor while installing?

If I have to "reinstall" can I do it this way:

All Primary Partitions

10.00G = Primary Partition - **BOOT** (nothing on it; for W2K at some point I feel like installing, it because my ISP doesn't support Linux)
10.0G = /
30.0G = /home
28.5G = /something for me to use
01.5G = swap - shows as: 1.43G

I have the SuperGRUB Disk so I'm not to worried about installing W2K "after" Linux.

Any help appreciated.
Have a Nice Day
Bruce

---

### Post by pytheas22 on 2008-04-26
I'm not an expert in these things, but I think that this is what you'd need to do:

1. edit /etc/fstab and comment-out the line pertaining to the partition currently serving as /usr (e.g. the one whose mount point is marked "/usr")
2. boot to the live CD, mount the two hard-disk partitions for / and /usr, and then copy the current contents of /usr  to / , under a directory named /usr (on / ).  For instance, if /dev/sda1 = / and /dev/sda2 = /usr , you would do something like this:

mount /dev/sda1 /media/sda1
mount /dev/sda2 /media/sda2
mkdir /media/sda1/usr
cp /media/sda2/* /media/sda1/usr

After this, the partition formerly used for /usr could be reformatted or merged with another partition or whatever you want, either using a live CD or gparted from within your system.  If you want it to be automatically remounted, you would need to edit fstab appropriately.

The only potential problem that I can think of is with permissions; in principle these should be copied over properly along with the files, but if not, things could get messy.  But I guess that if your alternative is to reinstall the whole system, it can't hurt to try this method first and if it fails, you just reinstall anyway.  In principle I'm pretty sure it should work, however.

If I should clarify anything, please let me know.

---

### Post by p_quarles on 2008-04-26
Yeah, the above suggestion will work. Just make sure to back up any data on partitions that you want to manipulate. In other words, if you plan on adding the new unused space to your /home partition, make sure everything on your /home partition is backed up first!

In any case, I think it would be simpler to simply shrink the /usr partition to a more reasonable size (say, 8 gigabytes), and either add the freed space to /home, or create a new data partition. 

One thing to remember is that /usr is where the vast majority of executables sit. As such, it tends to get bigger than most other parts of the / filesystem, especially for desktop/workstation computers. It's not all that terrible of an idea to have a separate partition for it. Not necessary, but not a terrible idea, either.

---

### Post by Bruce M. on 2008-04-26
> **pytheas22 said:**
> I'm not an expert in these things, but I think that this is what you'd need to do:

EXPERT:
ex - a "has been"
pert (pronounced: spert) - a drip under pressure

So glad to hear you are not one.
And a BIG *thanks for responding*.

> **pytheas22 said:**
> 1. edit /etc/fstab and comment-out the line pertaining to the partition currently serving as /usr (e.g. the one whose mount point is marked "/usr")
2. boot to the live CD, mount the two hard-disk partitions for / and /usr, and then copy the current contents of /usr  to / , under a directory named /usr (on / ).  For instance, if /dev/sda1 = / and /dev/sda2 = /usr , you would do something like this:

mount /dev/sda1 /media/sda1
mount /dev/sda2 /media/sda2
mkdir /media/sda1/usr
cp /media/sda2/* /media/sda1/usr

After this, the partition formerly used for /usr could be reformatted or merged with another partition or whatever you want, either using a live CD or gparted from within your system.  If you want it to be automatically remounted, you would need to edit fstab appropriately.

The only potential problem that I can think of is with permissions; in principle these should be copied over properly along with the files, but if not, things could get messy.  But I guess that if your alternative is to reinstall the whole system, it can't hurt to try this method first and if it fails, you just reinstall anyway.  In principle I'm pretty sure it should work, however.

If I should clarify anything, please let me know.

OK ... I'm looking at GParted here:

```
/dev/sda6 is my /
/dev/sda7 is my /home
/dev/sda8 is my /usr
/dev/sda5 is my linux-swap
```
From the "Live CD" (I have that too) I issue the command:
```
mount mount /dev/sda6 /media/sda6
```
Why the second part? "/media/sda6"

Would I not need to use "sudo" to mount these from the Live CD and or at least use "sudo cp" to keep permissions?
```
sudo mount /dev/sda6 /media/sda6 (my / )
sudo mount /dev/sda8 /media/sda8 (my /usr )
sudo mkdir /media/sda6/usr
sudo cp /media/sda8/* /media/sda6/usr

```

Thoughts..
Have a nice evening
Bruce

---

### Post by pytheas22 on 2008-04-26
> Why the second part? "/media/sda6"

the second part of the mount command tells the system where to mount the filesystem.  It could be anything, but Ubuntu uses the /media directory--a lot of other distros use /mnt.  On that note, if you get an error message about the directory not existing, it just means that you need to create it first (sudo mkdir /media/sda6).  I think Ubuntu might do this automatically now but I'm not positive.

> Would I not need to use "sudo" to mount these from the Live CD and or at least use "sudo cp" to keep permissions?

right, you'd need sudo to run these commands.

But yes, basically you'd do:
```

sudo -s
mkdir /media/sda6
mkdir/media/sda8
mount /dev/sda6 /media/sda6
mount /dev/sda8 /media/sda8
mkdir /media/sda6/usr
cp /media/sda8/* /media/sda6/usr
```

Also, I echo the other poster's reminder to back up important stuff first whenever you play with partitions.  I've never had a problem but I certainly wouldn't want one.

---

### Post by fragos on 2008-04-26
I may be wrong on this but, I'd make a /usrnew folder where /usr belongs and then copy the contents to it. Edit /etc/fstab to remove the /usr mount point and then rename /usrnew to /usr. Reboot and then you can deal with the old /usr partition which won't be mounted.

---

### Post by Bruce M. on 2008-04-26
> **p_quarles said:**
> Yeah, the above suggestion will work. Just make sure to back up any data on partitions that you want to manipulate. In other words, if you plan on adding the new unused space to your /home partition, make sure everything on your /home partition is backed up first!

In any case, I think it would be simpler to simply shrink the /usr partition to a more reasonable size (say, 8 gigabytes), and either add the freed space to /home, or create a new data partition. 

One thing to remember is that /usr is where the vast majority of executables sit. As such, it tends to get bigger than most other parts of the / filesystem, especially for desktop/workstation computers. It's not all that terrible of an idea to have a separate partition for it. Not necessary, but not a terrible idea, either.

Thanks for clearing this up, it came in as I was answering the same post.

Shrinking it? Now that sound interesting.
How does one do that? If I choose to go that route.

Beginning to think my /home at 30G is a bit of an over kill, as I said, I don't keep much there. However if I move /usr back to / it's going to be tight as / only has 9.3G now.

Maybe re-installing isn't such a bad option either:

10G for W2k (in the future if I feel like it of need it)
15G for / (with /usr)
15G for home
and about 45G left over less the 1.5G for swap.

This install is only two days old, not much on it yet, and I have 6 daily backups on my second HD as well as well as all my personal stuff. My .mozilla and .mozilla-thunderbird get sync'ed to the second drive every hour as well, so I'm not going to loose mail or bookmarks.

But I'm still thinking:
Shrinking it? Now that sound interesting.
How does one do that? If I choose to go that route.

BTW; I have the "Bootable GParted" .ISO here that I plan on burning to a CD. Again on my 2nd HD (40G of pure space)

Thanks
Have a good evening
Bruce

---

### Post by p_quarles on 2008-04-26
> **Bruce M. said:**
> But I'm still thinking:
Shrinking it? Now that sound interesting.
How does one do that? If I choose to go that route.

BTW; I have the "Bootable GParted" .ISO here that I plan on burning to a CD. Again on my 2nd HD (40G of pure space)
The bootable GParted disk will make shrinking and expanding partitions very easy. Just boot that up and you'll see how it's done.

Again, be sure to back up anything you don't want to lose A) always; and B) before editing the partition table. GParted is a great a very low-risk application, but partitioning is a fundamentally unstable operation.

---

### Post by Bruce M. on 2008-04-29
Well, when I started with:
```
sudo mount /dev/sda6 /media/sda6
```
I got an error that said:

/media/sda6 didn't exist.

So I did the simplest thing: I re-installed, as it was a "clean" install only a couple of days old.

Sorry to have bothered you all.

Have a nice day.
Bruce

---

### Post by p_quarles on 2008-04-29
> **Bruce M. said:**
> Well, when I started with:
```
sudo mount /dev/sda6 /media/sda6
```
I got an error that said:

/media/sda6 didn't exist.
I know you've already dealt with this, but for future reference, solving this problem is as easy as creating a mount point and then setting permissions for it:
```
sudo mkdir /media/sda6
sudo chown *username* /media/sda6
```
Then, the command you tried above will work just fine. 

> Sorry to have bothered you all.
Pshaw. Asking is the best way to learn.

---

### Post by Bruce M. on 2008-04-29
> **p_quarles said:**
> I know you've already dealt with this, but for future reference, solving this problem is as easy as creating a mount point and then setting permissions for it:
```
sudo mkdir /media/sda6
sudo chown *username* /media/sda6
```
Then, the command you tried above will work just fine.

AAAAAAAAAHHHHHHHHHHAA!
I would never have thought of that as I have access to those.

But I know better now. **Thanks p_quarles**
Another point to files away in my ever growing tips and tricks.  :)

> **p_quarles said:**
> Pshaw. Asking is the best way to learn.

Yea, like the first line of my sig has said since day one of being here.

If is wasn't for the [Search] Button, there'd probably be a hundred more questions from me. :lolflag:

Thanks again
CHIMO!
Bruce

---

### Post by Bruce M. on 2008-04-29
> **fragos said:**
> I may be wrong on this but, I'd make a /usrnew folder where /usr belongs and then copy the contents to it. Edit /etc/fstab to remove the /usr mount point and then rename /usrnew to /usr. Reboot and then you can deal with the old /usr partition which won't be mounted.

I should have looked at this a little close too.

I'm going to file this away as well, and "test" it some time.

Thanks for the tip.
Bruce

---

