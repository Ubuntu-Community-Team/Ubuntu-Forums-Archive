---
title: "Recovering my old files under Kubuntu"
date: 2020-02-17
forum: General Help
---

### Post by dj1100rt on 2020-02-17
I have an old PC running an earlier Ubuntu (14.04, I believe).  I did something months ago and it quit booting up.  Anyway, I created a LiveCD of Kubuntu 18 and have it running from a usb flash drive.  

My goal is to recover my old music and pics AND get Kubuntu (Ubuntu) running again.  I can see them from the temporary Kubuntu just fine.  Do I need to off-load them onto another drive before I install Kubuntu, or will my files still be there after I install the new desktop?

Thanks.
David

---

### Post by CelticWarrior on 2020-02-17
Just copy therm to another drive. It's a process called backup that should be in everyone's to do list. If you have done it before surely you wouldn't be asking now.

Regarding reinstallation, Kubuntu can be heavy for a very old PC but if it used to run Kubuntu 14.04 acceptably it'll run the same or better with the current release. So, backup and install fresh (there's no point it trying to upgrade from 14.04 now).

---

### Post by SeijiSensei on 2020-02-17
In the future consider creating a separate partition for /home. Then keep your files there. That lets you replace your Linux OS while keeping your files intact.

---

### Post by dj1100rt on 2020-02-18
> **SeijiSensei said:**
> In the future consider creating a separate partition for /home. Then keep your files there. That lets you replace your Linux OS while keeping your files intact.

Sounds good.  I’ll have to figure out how to do that.  

I do have 2 partitions, one for Win XP, and one for Ubuntu.  Thinking about wiping out windows after I save files and pics from both sides.  Picked up a 256 gig flash drive as the momentary file backup.

---

### Post by CatKiller on 2020-02-18
> **dj1100rt said:**
> Sounds good.  I’ll have to figure out how to do that.

It's easiest when you're doing a fresh install (like now!). During the install you choose Something Else, create your two partitions - a smallish one and a big one, usually - and set / as the mount point for the smallest one and /home as the mount point for the big one. It's doable post-install, but more fiddly. Your config files, documents, media, Steam games, and so on, are in your Home directory; your normal applications installed through the package manager would be on the / partition.

If you reinstall in the future you can set your /home partition's mount point but not format it, so then all your config files and whatnot will be preserved and available. That doesn't mean that you shouldn't do backups, though.

---

### Post by Impavidus on 2020-02-19
That smallish partition should be at least 15GB, but there's no need to make it bigger than 25GB. Which is still tiny on a modern hard drive, so there isn't much reason to make it much smaller.

---

### Post by mörgæs on 2020-02-20
> **dj1100rt said:**
> 
I do have 2 partitions, one for Win XP, and one for Ubuntu.  Thinking about wiping out windows...

It's easier to select 'erase everything' (or 'something else' as suggested above if you want a separate /home) when you install the new Buntu.

Both XP and 14.04 have been unsupported for some years. When you have installed a supported OS I suggest that you change all passwords which have been entered into a browser.

---

### Post by dj1100rt on 2020-02-22
Thanks to all of you.  I did copy all docs, pics and music from both sides to a large flash drive yesterday.  So, now we&#8217;re free to modify it as we want.

Question, it has an AMD64 processor and was running WinXP Home Media (which is always 32 bit).  I am free to go for a 64 bit Kubuntu, now, right?  (2 gig ram, though). Or do you think it will choke?

---

### Post by CatKiller on 2020-02-22
You should run 64-bit. 32-bit install images are no longer available, and 32-bit software is being phased out.

The OS and most applications will be OK in 2 GB RAM, provided you don't run many applications at once, but browsers are *heavy*. You'll likely find it beneficial to run extensions to limit the ability of websites to eat up your RAM with arbitrary programs. Install more RAM if you can.

---

### Post by dj1100rt on 2020-02-22
Thanks, catkiller.  One more question:  With 2 partitions, how should I proceed?  Reformat the whole drive, first, then install?

---

### Post by SeijiSensei on 2020-02-22
I'd choose the manual option when you get to the partitioning step in the installer.  Allocate some 30 GB for the "root" partition, the one where all the operating system is stored. Create a second partition using the rest of the space. Tell the installer to format both partitions with Ext4 and assign the small one to "/" and the large one to /home.

After the installation is complete you can copy your saved files to /home/yourusername.

---

