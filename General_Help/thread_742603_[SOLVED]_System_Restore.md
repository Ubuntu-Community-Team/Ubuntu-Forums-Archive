---
title: "[SOLVED] System Restore"
date: 2008-04-01
forum: General Help
---

### Post by DGortze380 on 2008-04-01
I've looked around and found a few option, but I'm not too sure still.

I've got an install of Ubuntu on my MacBook that's working fine, Desktop Effects, Wireless, all the drivers I need etc...

I'm a Computer Systems major and am continually breaking stuff while playing with linux. Because the laptop is also my everyday machine, I would like to be able to have a backup of a working install that I could easily restore.  I've looked at a few utilities that create live cd, but they all seem to skip drivers when making the cd.

I was thinking of putting an ISO on my external, booting from a live cd, then just writing the image to my existing partition. But I'm not sure how I'd go about doing that.  

My other option I guess would be just backing up my / partition on the external, booting from a live disk, and deleting everything on the partition and dropping my backup onto the clean partition.

Would either of these option work? Is there a better way to do this?

-Dan

---

### Post by dcstar on 2008-04-01
> **DGortze380 said:**
> I've looked around and found a few option, but I'm not too sure still.

I've got an install of Ubuntu on my MacBook that's working fine, Desktop Effects, Wireless, all the drivers I need etc...

I'm a Computer Systems major and am continually breaking stuff while playing with linux. Because the laptop is also my everyday machine, I would like to be able to have a backup of a working install that I could easily restore.  I've looked at a few utilities that create live cd, but they all seem to skip drivers when making the cd.

I was thinking of putting an ISO on my external, booting from a live cd, then just writing the image to my existing partition. But I'm not sure how I'd go about doing that.  

My other option I guess would be just backing up my / partition on the external, booting from a live disk, and deleting everything on the partition and dropping my backup onto the clean partition.

Would either of these option work? Is there a better way to do this?

-Dan

"Clean" partitions invariably have different UUIDs to the ones configured into an existing system, so image restores will have issues until you change the UUIDs to match.

This is an issue with moving/restoring anything with a partition "snapshot" these days. so keep it in mind if you go down that path.

---

### Post by GuitarRocker2562 on 2008-04-01
I am 90% sure that copying your / partition to an external would work great, if the external was formattted as an ext3. Just to let you know, if you don't have a seperate /home partition, I would do that immediately.

---

### Post by LaRoza on 2008-04-01
> **DGortze380 said:**
> 
I'm a Computer Systems major and am continually breaking stuff while playing with linux. Because the laptop is also my everyday machine, I would like to be able to have a backup of a working install that I could easily restore.  I've looked at a few utilities that create live cd, but they all seem to skip drivers when making the cd.

I was thinking of putting an ISO on my external, booting from a live cd, then just writing the image to my existing partition. But I'm not sure how I'd go about doing that.  

My other option I guess would be just backing up my / partition on the external, booting from a live disk, and deleting everything on the partition and dropping my backup onto the clean partition.

Would either of these option work? Is there a better way to do this?

-Dan

Would it be possible to use another internal drive? It would make things easier. See: [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/) for making a full backup.

If you have the RAM, a virtual machine would be most useful.

You can backup your home directory (for your settings) and use aptoncd to make a cd with all your installed packages.

I wrote a script which can reinstall all packages as well, but aptoncd would be best for this.

---

### Post by ryanhaigh on 2008-04-01
Here are some imaging solutions you might want to look at:
[www.partimage.org](www.partimage.org)
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

I personally use the proprietary Acronis TrueImage which I already own for imaging windows pcs. I have never had problems with UUIDs when using imaging software as the partition restored is identical (assuming you keep the same size on restore). In fact I read once on these forums that people were having trouble with their partitions because they had restored to a new HD while keeping the original partition as well, two partitions with same UUID = grub/fstab confused. In my experience the use of UUIDs for grub and fstab is a PITA I would prefer the old method using /dev/sd*.

---

### Post by Tews on 2008-04-02
Actually, there is a program available that will do all that you are asking called Quick-Start.  

[IMG]http://www.libertymanor.org/menu.png[/IMG]

As you can see from the main menu, there is quite a lot that you are able to do.  I am a "tweak junkie", but sometimes my "tweaks" have results that breaks things.  I run Quick-Start and can restore my system  to its backed up state in about 30 minutes.  You can read more about it here ===>> 

[http://ubuntuforums.org/showthread.php?t=613462]("http://ubuntuforums.org/showthread.php?t=613462")

Hope this helps

---

### Post by DGortze380 on 2008-04-02
thanks for all the replies. I'll take a look at everything and see what works best for me, quick start looks intriguing.

---

