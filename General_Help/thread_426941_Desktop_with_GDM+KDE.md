---
title: "Desktop with GDM+KDE"
date: 2007-04-29
forum: General Help
---

### Post by Imsati on 2007-04-29
Regarding my thread here, [http://ubuntuforums.org/showthread.php?t=426849](http://ubuntuforums.org/showthread.php?t=426849) I made 2 15 GB partitions (one for Gnome, one for KDE) and a shared Swap/Home.

Problem is, seeing as how my Home (and thus Desktop) is shared, my GNome apps show up as dead links in KDE and vica versa. Is there a way I can set up my partitions to prevent this from happening?

Could I have Gnome + Home, KDE + Home, then a shared partition that acts like Home where I can keep all my music and personal files on? I'd really like to keep the Desktops completely separate.

--Jay

---

### Post by Nythain on 2007-04-29
gnome and its home partition, kde and its seperate home partition, and another partition mounted somewhere like /data should work well... just make sure that both users have read/write/execute access too it, you could try creating a new group specifically for that mount, add both users to the group and that should work well... hopefully...

---

### Post by fwojciec on 2007-04-29
> **Imsati said:**
> Could I have Gnome + Home, KDE + Home, then a shared partition that acts like Home where I can keep all my music and personal files on? I'd really like to keep the Desktops completely separate.

That would definitely work.  My computer is set up similarly to share files between Windows and 2 Linux partitions - I use a fat32 volume for sharing (it is actually a separate hard drive), but you could use ext3 partition, which would work even better (fat32 can be annoying).  If you use Mozilla applications you can save Firefox/Mozilla profiles on that partition and use them in both Ubuntu and Kubuntu - that way your bookmarks, mail and so on are always up to date and available regardless of which version of Ubuntu you're accessing them from.  Same with music - I have Quod Libet in Linuxes and Foobar in XP accessing the same Directory with all my music files.  Documents are stored in this way as well.  I also share that fat32 volume over network with Samba so that I can access it from my laptop as well ;)  It's a good solution.

---

### Post by Imsati on 2007-04-29
Good idea. When creating the /data (or whatever) partition to be shared, can I choose the name? The perfect end result would be Gnome and it's Home, KDE and it's Home, and Jason.

Going to bed now, I'll check back in the morning. Thanks!

---

### Post by Imsati on 2007-04-29
> **fwojciec said:**
> That would definitely work.  My computer is set up similarly to share files between Windows and 2 Linux partitions - I use a fat32 volume for sharing (it is actually a separate hard drive), but you could use ext3 partition, which would work even better (fat32 can be annoying).  If you use Mozilla applications you can save Firefox/Mozilla profiles on that partition and use them in both Ubuntu and Kubuntu - that way your bookmarks, mail and so on are always up to date and available regardless of which version of Ubuntu you're accessing them from.  Same with music - I have Quod Libet in Linuxes and Foobar in XP accessing the same Directory with all my music files.  Documents are stored in this way as well.  I also share that fat32 volume over network with Samba so that I can access it from my laptop as well ;)  It's a good solution.

Excellent. At least now I know it's possible and I just need to find the right settings.

---

### Post by Nythain on 2007-04-29
you can mount the partition wherever you want... you're not so much naming it (though you can give it a name in the label section when you create the partion) as you are creating a place for it to sit... you could sudo mkdir /jason and mount it there, or /stuff, im not to sure, but if you set the permissions right you could probably just sudo mkdir /home/jason and mount it there... if you dont have any users or plan on having any users named jason... the moral of the story, you can create any folder you want just about anywhere in your system to mount the shared storage partition at... once you get the partition created, and make the location to mount it, give us some more info and we'll help you set up your fstab to mount it automantically and also help you set up the permissions so you can access it from both de's

---

### Post by Imsati on 2007-04-29
> **Nythain said:**
> you can mount the partition wherever you want... you're not so much naming it (though you can give it a name in the label section when you create the partion) as you are creating a place for it to sit... you could sudo mkdir /jason and mount it there, or /stuff, im not to sure, but if you set the permissions right you could probably just sudo mkdir /home/jason and mount it there... if you dont have any users or plan on having any users named jason... the moral of the story, you can create any folder you want just about anywhere in your system to mount the shared storage partition at... once you get the partition created, and make the location to mount it, give us some more info and we'll help you set up your fstab to mount it automantically and also help you set up the permissions so you can access it from both de's

Well, I'll have to make a new partition for the 'Jason' area. How would I mount it during an install? I'll install Ubuntu first as I prefer it's installer, and I'll set up six partitions (Swap, both OS's, both Homes, my area).

--Jay

---

### Post by Imsati on 2007-04-29
Bump. Any thoughts as to how I should mount my partition with all my personal stuff?

---

### Post by fwojciec on 2007-04-29
You can choose which partitions will be mounted during install.  Choose "partition manually" (or whatever that option is called in the installer) and assign mount points for the available partitions:

the partition you choose for your root should be assigned to: "/" (and formated)
home partition: "/home"

I put all my other partitions into "/media" directory so in my case, for example
/dev/sda1 is assigned to "/media/windows"
/dev/sda5 is assigned to "/media/linux2"

If you have two swap partitions make sure that you select "don't use" as a mount point for one of them (if you want to keep separate swap partitions for both your Linux installations.

That's it.  All the partitions you specify mount points for during installation will be available in when you boot your new system, they might not be writable by default though.  To be honest, I don't remember exactly how to change that - maybe it's enough to specify a moun point within your /home directory (I'm not sure about that).  Just search the forums/google for "mount ext3 writable feisty" or something like that and you should find the solution.

Good luck!

---

