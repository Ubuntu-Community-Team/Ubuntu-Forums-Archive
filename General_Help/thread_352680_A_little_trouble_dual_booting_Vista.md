---
title: "A little trouble dual booting Vista"
date: 2007-02-03
forum: General Help
---

### Post by sarc on 2007-02-03
I got an HP pavilion DV6000 that came with Vista preinstalled.  The user wants Windows, so I completed the Vista installation with little trouble.  Then I want to install Edgy for dual boot (already did that in Windows XP).

Before starting, I already hit trouble: Vista will not let me resize the primary partition to make room for Edgy.  The hard disk is 120GB and the space used is less than 11GB.  But at most I can shrink the primary partition to a little less than 60GB, wasting 50GB to Vista in the process.

I could try using GParted from LiveCD but I don't know if Vista will like the result.  I cannot afford disaster as it's not my computer.  Any experience out there?  Why will Vista not let me shrink the primary to a reasonable size?  And can I use Gparted without breaking Vista?  Thanks

---

### Post by dexter on 2007-02-03
> **sarc said:**
> I got an HP pavilion DV6000 that came with Vista preinstalled.  The user wants Windows, so I completed the Vista installation with little trouble.  Then I want to install Edgy for dual boot (already did that in Windows XP).

Before starting, I already hit trouble: Vista will not let me resize the primary partition to make room for Edgy.  The hard disk is 120GB and the space used is less than 11GB.  But at most I can shrink the primary partition to a little less than 60GB, wasting 50GB to Vista in the process.

I could try using GParted from LiveCD but I don't know if Vista will like the result.  I cannot afford disaster as it's not my computer.  Any experience out there?  Why will Vista not let me shrink the primary to a reasonable size?  And can I use Gparted without breaking Vista?  Thanks

What do you use to resize the partitions in windows ? As far as a know, windows never came along with a partition resizer. In windows you can try Partition Magic which should do the trick.

But you can also use the live cd (and gparted) or the setup to resize the hard disks. I did not fail here (although i don't have vista but xp, but i can't see why vista would be messed up by it).

---

### Post by sarc on 2007-02-03
Vista has a Partition Manager in Manage My Computer - Storage - Archive - Compress (or something like that) that lets you resize partitions.  The online docs confirm that it is a partition resizer, not a file compress utility.

More news.  I cannot run the LiveCD Edgy 6.10 on the HP Pavilion dv6000.  About half way to boot I get a few error messages 'kernel [something] missing or cannot be loaded (too fast to read), then the screen goes blank.  Tried an original CD and one I burned myself - same problem.  I installed Edgy on an HP pavilion DV2000 no problem.  Help.

---

### Post by sarc on 2007-02-04
BUMP BUMP! Help!

---

### Post by TNBY963 on 2007-02-05
Hi,

I dual boot Vista with Ubuntu Edgy. 
I first installed vista and then repartitioned my drive with gparted. However, Vista didn't like that and I had to reïnstall it again.
So the process that works for me is: Install Vista > In the install phase tell it to only use the amount of memory that you want (20 gig or so) and leave the rest unpartitioned. > After the installation you can install Ubuntu on the unpartitioned part of your drive and grub will recognize Vista and put in in the boot menu. This worked for me at least.
I can't help you with your cd problem. That I know nothing about.

---

### Post by sarc on 2007-02-05
Ach!  Bill must have gotten smart because this time Vista did not give me any choice of how much disk space to use (it came preinstalled with the PC).

So gparted does not work with the BillVirus.  Anyone had success reducing a Vista primary partition?

---

