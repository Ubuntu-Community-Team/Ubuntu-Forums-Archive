---
title: "Moving / partition contents"
date: 2006-11-04
forum: General Help
---

### Post by xdevnull on 2006-11-04
This may seem a little crazy, but I'd like to move everything except my home directory to another partition.  Evidently I made an error when I was installing.  I created two partitions, one 15Gig /dev/hda5 which was supposed to hold everything except /home, which was then to be mounted on another partition which is 50Gig /dev/hda6.  For some reason, everything installed on the 50Gig drive...

/dev/hda5 - mounted /media/hda5 - use=129M - lost+found and nothing there (15G)
/dev/hda6 - mounted / - everything including home. (50G)

What I would like to do is move everything except /home to /dev/hda5 and mount it as root:

/dev/hda5 mounted at /
/dev/hda6 mounted at /home

So I was going to drop to init 1, cp -ax everything except /home to /media/hda5.  I'm not sure if there is a handy expression for copying everything except a particular file/directory.  Maybe someone knows.  Then edit fstab to mount /dev/hda5 to / and /dev/hda6 to /home, move my home files and give it a boot.  I'd keep everything else on /dev/hda6 the same for now in case something doesn't work, I can revert.

The thing is, I'm not sure if there is anything weird in the / partition (some boot file or the like) that would prevent me from then starting the system properly.  Or other weirdness.   Hopefully the more experienced users can advise me on potential problems.  Obviously I need to make sure to edit the fstab on the new mount point before restarting or not much will be accomplished.

```
init 1
cd /
cp -ax *(except home) /media/hda5
mkdir /media/hda5/home
cd /media/hda5/etc
vi fstab (make switches)
mount -a
```
Now there are two possibilities to getting the home directory right.  Not sure if mv will keep the permissions.
```
mv /home/home/bg /home/bg 
or 
cp -ax /home/home/bg /home/bg
then
rm -R /home/home/bg
init 5

```

What am I leaving out?

---

### Post by CatKiller on 2006-11-04
I think you probably know more than me, since you appear to know how to use init. But the critical bit that you've forgotten so far, as far as I can see, is GRUB. You'll need to update that to boot from the right partition.

Also, it might be best to do all of this from a live cd environment. Just in case.

I'd also be tempted to use **dd** to do the copy, and then mount the old partition's /home on /home. Or use **tar** to do the copy. You can tell tar to exclude a file or directory, but I don't know how. Here's the start of a tar command that you might find useful though: ```
( cd <source> && tar clf - . ) | ( cd <dest> && tar xvpf - )
```

---

