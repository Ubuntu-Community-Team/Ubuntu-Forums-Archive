---
title: "Any good advice on backing up Linux ?"
date: 2014-08-05
forum: General Help
---

### Post by firas2 on 2014-08-05
Good day 

I have Ubuntu on a Virtual Machine   and I would Like to know what is a good method of backing up Ubuntu ?

I have plenty of room on my  physical pc  , not sure but i was thinking an ISO  or something like that 

and if so and things do go wrong  will i be able to just recover through my Virtual machine ??


any recommendations

  
thank you

---

### Post by TheFu on 2014-08-05
If using virtualbox - File - Export.
You can backup a VM just like it is a real physical machine install too - must be 50 different ways, so "good" is relative to your RTO/RPO requirements.

You can clone any Linux install using partimage, clonezilla, fsarchive, dd, and/or probably 15 other options.  I think cloning an install is a waste, but many people prefer that method. Just connect another ISO to the VM and boot off that to ensure /dev/sda1 isn't mounted.

If you are running LVM - snapshots are an option, but getting the data to a different physical disk is needed.

[http://ubuntuguide.org/wiki/Ubuntu_Trusty_System_Backup](http://ubuntuguide.org/wiki/Ubuntu_Trusty_System_Backup) is a good place to read about the options in more detail.

---

### Post by firas2 on 2014-08-05
Thank u sir for ur fast respond  But my concern is would i be able to recover it through the VM   I have not don that before therefor I am asking 

thanks for the Link

---

### Post by firas2 on 2014-08-05
snapshot worked like a charm  but cant find how to move it to physical hdd  :p

FOUND EVERY THING   SOLVED 

 thank u sir

---

### Post by TheFu on 2014-08-05
VM-based snapshots ARE NOT backup methods.
LVM-based snapshots can be used as an aid to backups, but they are NOT a backup either.

If you specify which VM program you are using, there may be specific answers that are relatively easy.

---

### Post by firas2 on 2014-08-05
VMware Workstation 10

Im pretty sure there will be something on there website 

I just haven't had the time  yet  still Buzzing from reading all about Linux ;)

---

### Post by TheFu on 2014-08-05
Most people here will be using 
* virtualbox
* KVM
* VMware Player
* Xen
* VMware ESXi / vsphere

So - if you want a VMware Workstation-specific answer - best to hit the VMware.com forums.

---

### Post by firas2 on 2014-08-05
> **TheFu said:**
> Most people here will be using 
* virtualbox
* KVM
* VMware Player
* Xen
* VMware ESXi / vsphere

So - if you want a VMware Workstation-specific answer - best to hit the VMware.com forums.


thanks  will do

---

