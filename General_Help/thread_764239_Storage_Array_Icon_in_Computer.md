---
title: "Storage Array Icon in Computer"
date: 2008-04-23
forum: General Help
---

### Post by Kissell on 2008-04-23
I have a RAID volume mounted in the /mnt folder and in the fstab file.

Now when I click on "Computer" the address bar says "computer:///" and there is an icon for a storage array there, but the icon doesn't work.

However, if I goto "Filesystem" then browse to the /mnt folder I can access the data on my array.  

How do I fix that icon to make it work?

---

### Post by chrisccoulson on 2008-04-23
Is the RAID volume using dedicated hardware RAID, BIOS software RAID (aka FakeRAID), or Linux software RAID? What RAID level is the volume?

---

### Post by Kissell on 2008-04-23
I created a linux software raid using mdadm.

It's eleven 750gb disks in a raid-6.  

raid is healthy and active, i've been using it just fine...  i just have to go to the mount point to use it, and it puts an icon under computer that doesn't work...  

oh, i'm also running Hardy 8.04...  i believe that's when the non-working icon showed up in COMPUTER was when i upgraded.

where is "Computer:///" at on the disk?  is there like a folder where those icon shortcuts are stored, or a file similar to fstab which identifies the things which shoow up under COMPUTER and how they show up and how they function?

---

