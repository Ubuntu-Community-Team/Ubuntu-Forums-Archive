---
title: "Partitioning Tips"
date: 2008-05-13
forum: General Help
---

### Post by genobambino on 2008-05-13
I have been testing out both XP Pro x64 and Kubuntu Hardy on my HP Pavilion dv9420us. I like both of them, and am going to make a more permanent setup in terms of partitions.

This laptop has two 120 GB hard drives, which I currently have set up as such:

Drive 1
30 GB partition for XP
60 GB partition for music
4 GB (double my ram size) swap partition for Kubuntu at the end of the drive

Drive 2
100 MB partition for /boot
30 GB partition for /

I am going to reinstall both XP and (K)Ubuntu to clean up after all of my trial and error. I am looking for tips on how to plan out the partitions for the new configuration, like how much size for XP, how much for Kubuntu, where to put all of the partitions, should I use separate ones for /home, /var, /tmp, ect...
Thanks!
Gene Merewether

---

### Post by Zorael on 2008-05-14
I imagine it might be a different case if you want higher data security, such as in a server environment, but I only break out /home into its own partition.

On this (Kubuntu) installation I made root 15gb, and now - a ~month after Hardy release and thus after installation - I realize I should've made it at least 20gb. 15gb is fine until you start wanting to compile your own kernels, try out KDE4, and similar stuff.

---

### Post by az on 2008-05-14
Putting everything on one partition is the only way to maximize your flexibility.  You will not run out of space that way.  

Anyway, there is no good reason to keep a separate home partition on a desktop these days.  It's far easier and safer to make a proper backup.

There is no reason to keep a separate boot or other partition either.  One root and one swap partition is what I recommend.  You can keep a separate partition for your music if you like, but don't make that a /home partition.

---

### Post by shifty_powers on 2008-05-14
well personally, always had /boot (100 meg), / (i.e. root and 5-10 gig), and /home (evrything else). This is not including swap of course. just habit i suppose, but works well for me ;)

---

### Post by talz13 on 2008-05-14
> **az said:**
> Putting everything on one partition is the only way to maximize your flexibility.  You will not run out of space that way.  

[color=red]Anyway, there is no good reason to keep a separate home partition on a desktop these days.  It's far easier and safer to make a proper backup.[/color]

There is no reason to keep a separate boot or other partition either.  One root and one swap partition is what I recommend.  You can keep a separate partition for your music if you like, but don't make that a /home partition.

I respectfully disagree there...  I always make home its own partition.  I mean, you really don't need that much space for root on most systems.  On my 1TB LVM, I gave root 5GB, plenty of space left for whatever might need it.

Now, when I reformat/reinstall/change distros/ whatever, I just blow away the root partition, install, and point back at my home partition.

I do make backups nightly, but why should I have to go through the process of a data restore if I don't need to?

I say just make root 5-10GB, then devote the rest to your home partition.  That's where you keep all your data anyway, right?

---

### Post by az on 2008-05-14
> **talz13 said:**
> I respectfully disagree there...  I always make home its own partition.  I mean, you really don't need that much space for root on most systems.  On my 1TB LVM, I gave root 5GB, plenty of space left for whatever might need it.

Well, a dist-upgrade saves downloaded packages in /var/cache.  There are plenty of applications that will use /lib /var and /tmp and those can account for a few gigs of space pretty fast.  It really depends on what you do.  If you don't want to have to worry about this, don't create separate partitions unless you have a really good reason to do so.

> **talz13 said:**
> 
Now, when I reformat/reinstall/change distros/ whatever, I just blow away the root partition, install, and point back at my home partition.

Sure, but it's often really useful to ditch your configurations if you've borked something up.  

Keeping a separate home can be done but it does increase the level of complexity (and risk of error - ever blown away the wrong partition?  Lot's of people do...)

> **talz13 said:**
> 
I do make backups nightly, but why should I have to go through the process of a data restore if I don't need to?


Nothing is more secure than a backup on a separate disk.  Even if you partition your disk, if the disk fails, you lost your data.

For me, the convenience of keeping something on a separate partition is not worth it.  I prefer something more straightforward and safe.

---

### Post by Oldsoldier2003 on 2008-05-14
I have to side with Az on this one. Over the last week I have installed tested and uninstalled several distros and have installed at least 30 (no kidding here) times. I bought into the separate home theory once, but the fact is that when you use multiple distros from multiple Linux "families" having a separate home does you absolutely no good. There is enough variation between the distros that your configs are gonna get borked unless you use a separate username for each distro- which basically just removes any advantage you have gained by having a separate home.

I find it better to simply have a separate data partition and symlink it to a folder in your home. 

Sharing /boot is a bad idea too... you will run into issues that will render your distros unbootable. I cant speak for everyone but a a separate data partition with your installations shoved into a single / works very well. The only time i would consider other separate partitions is in the case of mailservers that benefit from having a separate /var

---

### Post by Joeb454 on 2008-05-14
I'm siding with Oldsoldier, I think the only reason to have a separate home is if you're going to keep reinstalling the same OS :)

Separate /data partitions are the way to go (I'll have one when I have to reinstall)

---

