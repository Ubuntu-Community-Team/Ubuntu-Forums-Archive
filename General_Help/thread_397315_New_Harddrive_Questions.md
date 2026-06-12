---
title: "New Harddrive Questions"
date: 2007-03-30
forum: General Help
---

### Post by MonkeyBoy on 2007-03-30
At the moment I have an 80 gig hd with 3 main partitions:  Ubuntu, XP, and a shared fat32 space.  I have ordered a new 160 gig drive to add to my pc.  My hope is to put a new install of Ubuntu on the new hd, and keep the XP partition on the old hd.  I will probably make my old Ubuntu partition into more shared space.

My plan is to first install the new hd as master and shift the old hd to a slave plug.  Then I will intall Ubuntu on the new hd.

Are there any specific considerations I need to make before doing all this?  My concerns are will grub recognise my older hd's partitions (XP and old Ubuntu)?  And if not is it just a case of editing grub.conf to see my XP partition?  Also once I have copied everything useful from my old Ubuntu partition to the new one, am I correct in thinking that all I need to do is reformat the old partition and edit grub again?

I have never used 2 hds before so I thought I would ask as I don't want to bugger up my old hds data as it has a lot of photos, etc.

---

### Post by phidia on 2007-03-30
Making a drive change like that from master to slave will require some editing.
When people tell you, in these situations, to back up the data you wouldn't want to lose-it's good advice.

You will need to edit /etc/fstab to reflect the change in drive postion.
e.g. Say the drive is now /dev/hda with partitons hda1 and hda2 when the drive gets switched those partitions will be hdb1 and hdb2.

Grub will need to be edited too-check out a good grub how to on that.

---

### Post by MonkeyBoy on 2007-03-30
Surely if I delete my old Ubuntu partition before I start then the new Ubuntu installation on the new master hd will write the correct fstab based on the XP partition on the slave hd?  The XP partition will be the only bootable partition on the slave hd.

Does grub automagically search for bootable partitions on other hds in the pc?

---

### Post by ububaba on 2007-03-30
Let me tell from the start, I have used Ubuntu for quite a while yet am facing problems. I can not restart my Dapper Drake. It gets stuck at "...Uncompressing Linux".  Now I have decided to use a
new Sata HDD for installing DD LTS but unfortunately after these three statments of the Ubunutu
install screen, nothing happens further

[B][I]Loading essential drivers
Mounting root file system
Waiting for root file systems[/I][/B]

The wait goes on for hours without much happenning. Where do I go wrong?

---

