---
title: "How do I install apps on a secondary hard drive?"
date: 2008-06-14
forum: General Help
---

### Post by mjpatey on 2008-06-14
Hi, all-

Been a while since I've posted here... I'm now the proud owner of a little EeePC 900 mini-laptop.  I'm running a full Hardy install on it with an experimental custom kernel.  Hardy takes up 3GB of the 4GB of total space on my primary (system) drive.

The secondary internal drive gives me an additional 16GB of space, so I'd like to try installing some apps there.

Is there a way in Ubuntu to install a program to a drive other than the primary system drive?

Thanks for any insight you may have!

-Mark

---

### Post by p_quarles on 2008-06-14
I understand from your post that the secondary drive is permanent -- if that's incorrect, please disregard the following suggestion.

It should be as easy as mounting a partition from the secondary drive as /usr, or as /usr/bin. This will be the easiest way, as once you've made the filesystem table changes, installation and usage of apps will automatically work.

---

### Post by mjpatey on 2008-06-14
Yes, it is permanent.

So, if I understand correctly, I'd do:

```
sudo mount /dev/sdb1 /usr/bin
```

...then I'd have to move the contents of the old /usr/bin to the new location, and all new apps will install there automatically?

And all apps, old and new will run without a hitch this way?

And finally... is there a way to just run certain apps from this second drive, rather than every program on the machine?

Thanks for your help!!!

-Mark

---

### Post by p_quarles on 2008-06-14
> **mjpatey said:**
> Yes, it is permanent.

So, if I understand correctly, I'd do:

```
sudo mount /dev/sdb1 /usr/bin
```

...then I'd have to move the contents of the old /usr/bin to the new location, and all new apps will install there automatically?
You'd want to move the directory to the "/" directory of the new partition *before* mounting it as /usr/bin. That is, you'd want to use a boot disk for this, since you'll need to use applications that will have to be unmounted during the moving process. 

You will then want to add an entry to /etc/fstab to make this mounting scheme tak effect on bootup. It would look something like this:
```
/dev/sdb1 /usr/bin ext3 defaults 0 2
```

> And all apps, old and new will run without a hitch this way?
Yep. 

> And finally... is there a way to just run certain apps from this second drive, rather than every program on the machine?
I can think of a few ways to force the computer to do this, but none I would recommend.

EDIT: Just for the record, this won't move every single application to the new drive, just the vast majority of optional applications, and virtually every graphical application. The core utilities are in /bin, and many of the scripted utilities are in /sbin and /usr/sbin. None of those directories will be changed in this setup (which is a good thing -- messing with /bin is a bad idea, and it doesn't take up enough space to worry about).

---

### Post by mjpatey on 2008-06-14
Awesome.  Thanks a lot!  I'll try this ASAP and post back with results.  Thanks for the clear, concise information!!!

-Mark

---

### Post by yaknowwat on 2008-06-14
the eeePC hard drive is indeed quite small.

from the sounds of things you added a USB drive as the secondary storage. (more than likely using the extra internal usb lines)

It may be a better choice to do a different setup.

most of the space taken up in /usr is taken in /usr/lib not /usr/bin

The biggest parts on my system are

/var (this is around 2 GiB)

(/usr is around 4 GiB)
/usr/lib 
/usr/share
~of course that means /usr is one of the large folders because it contains 2 major folders.

/lib (almost a GiB)
(half of that is in /lib/modules)

then because of my usage these are the other large parts

/home ( since im on a desktop and use virtual machines tons of iso's ( i like to test linux distros sometimes) along with multimedia reasons this is taking around 50 GiB so yeah not typical usage there. )
/opt (i have about 10 applications installed into the opt directory its good for applications you dont want installed all over the system aka non packaged ones.)

I would suggest a different setup than what you were suggested personally.

Assuming your secondary storage is indeed a flash drive it wont be as fast as the built in 4GiB solid state drive but it is larger so that would mean in order to reduce load on your system its best to choose the directories that will go to the second storage wisely.

my suggestion would be to do multiple partitions on the flash drive.

then to add them into fstab (the standard ubuntu uses now for drives is UUID for mounting drive partitions)

If you don't mind having your home directory on the secondary storage i'd suggest this.

/home 9 GiB
/usr/lib 5 GiB
/usr/bin 1 GiB
/tmp 1 GiB

If you want your home directory to be more safe in case the flash drive fails then i'd suggest putting this onto the secondary drive

/usr 9 GiB
/var 6 GiB
/tmp 1 GiB

---

### Post by mjpatey on 2008-06-14
Thanks for all the info!

In the EeePC 900, there are actually 2 internal SSDs (solid state drives).  The second one (16GB) is a tad slower than the primary (4GB), but is obviously a lot roomier.

My objectives are to keep the primary drive from getting too full, and to give myself room to add applications as needed without running into the 4GB wall of the primary drive.

So I'm going to put /usr/bin and /home on the slower, but roomier, secondary drive.  That'll bring my current main drive down to about 2.8GB used (out of 4GB), which feels comfortable to me, and all new apps will be installed (and my personal data will be stored) on the secondary drive.

As there is a speed difference between the 2 drives, I don't want to put too much on the secondary one, as it'll probably slow my system down a bit more noticeably.  In fact, I may go back to the traditional setup after moving usr/bin if that slows it down too much by itself.  But thanks for the well-thought suggestions just the same!

-Mark

---

