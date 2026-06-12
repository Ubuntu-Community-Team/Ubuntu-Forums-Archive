---
title: "can I mount my old /var lvm in new install?"
date: 2016-07-28
forum: General Help
---

### Post by redking3 on 2016-07-28
I made a really really dumb mistake, and broke my root partition. 

so what I am wondering is, can I mount the LVM where /var was mounted in the old broken system as /var in the new install, and have the programs that I used working again?

---

### Post by TheFu on 2016-07-29
Yes.
Just mount the old LV to the /var/ directory.  Is there some issue doing that?  I've done this lots with and without encrypted partitions.  Just use the normal LVM commands to access the PVs, VGs, and LVs desired.

---

### Post by redking3 on 2016-07-29
> **TheFu said:**
> Yes.
Just mount the old LV to the /var/ directory.  Is there some issue doing that?  I've done this lots with and without encrypted partitions.  Just use the normal LVM commands to access the PVs, VGs, and LVs desired.

Thanks for the reply, just wasnt sure if it would actually work. first time with this kind of recovery. 

So there is no files other places in a linux machine that your programs need? as long as I use the same distro I can just mount the /var lvm in /etc/fstab and it just start working again?

just to make sure im not completly misunderstanding it all, but it is the programs I install and its configurasjons that are stored in the /var, correct?

with windows, this kind of recovery would never work, correct?

---

### Post by TheFu on 2016-07-29
/var is for for "variable data" ... shouldn't be any programs down there.  Just data.  You'll have to get LVM to recognize the PE, PV, VG before you can just mount the LV. But after that is setup, it should "just work."

The most common things I notice in /var/ are web sites, DBMS data files, virtual machines (if you use libvirt) and APT package stuff.  That doesn't mean there won't be issues.  I would only restore the files that I put there, if you asked me.

Can't answer any questions about Windows. I never expect any restores that aren't complete bit-for-bit across all non-data storage to work on Windows. Plus on Windows, any tiny change to the hardware will make it never work.  Whereas I've moved disks multiple times between completely different machines and booted Linux. Only a few small tweaks for udev were needed to make everything work as before.  For most people, it would be just to delete the eth0 line - that's it.  With systemd, that has changed and I don't have enough experience to know what would be needed. Different issue.

---

### Post by redking3 on 2016-07-29
> **TheFu said:**
> /var is for for "variable data" ... shouldn't be any programs down there.  Just data.  You'll have to get LVM to recognize the PE, PV, VG before you can just mount the LV. But after that is setup, it should "just work."

The most common things I notice in /var/ are web sites, DBMS data files, virtual machines (if you use libvirt) and APT package stuff.  That doesn't mean there won't be issues.  I would only restore the files that I put there, if you asked me.

Can't answer any questions about Windows. I never expect any restores that aren't complete bit-for-bit across all non-data storage to work on Windows. Plus on Windows, any tiny change to the hardware will make it never work.  Whereas I've moved disks multiple times between completely different machines and booted Linux. Only a few small tweaks for udev were needed to make everything work as before.  For most people, it would be just to delete the eth0 line - that's it.  With systemd, that has changed and I don't have enough experience to know what would be needed. Different issue.

Thanks for the reply! 

Yea it was the Virtual machines I wanted restored. not sure what "variable data" means, but this cleared the process for me I think.

Will just copy the machines to a USB and format the lvm before I move the contents of the new /var into the lvm, and mount it as /var

then ill just install the stuff again and copy the machines back.

Btw: its a really bad idea to setup ur / in a raid 0, and then passthrough one of those disks to a VM by mistake..... the raid 0 thing was also a mistake, was pretty sure I had set it up as raid 1 untill I found out there was no raid left at all

---

### Post by TheFu on 2016-07-29
I don't put my VMs under /var/.  Don't think that area should be more than a few hundred MB in size.

RAID is only good for HA.  It never replaces backups.  RAID solves 2 problems.  Backups solve 10,000 problems, including broken RAIDs. ;)

---

