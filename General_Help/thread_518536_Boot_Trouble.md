---
title: "Boot Trouble"
date: 2007-08-06
forum: General Help
---

### Post by cspclay on 2007-08-06
I installed wubi to a virtual machine using MS VPC.  I shut it down instead of rebooting when finished with the installation.  I ran some updates on my host computer and rebooted it when finished and I received a grub error screen saying it could not find the option for Windows Vista and kernel was not compiled to load ubuntu so it took me straight to command line.  I cannot get my windows on my host machine to boot after installing wubi to a virtual.  Not quite sure what to do from here.  I booted to recovery console and ran chkdsk and even tried a system restore to no avail.  To run the system restore I had to run it "offline" because the windows recovery console did not recognize my windows installation anymore.  I noticed on my root drive a grldr file but could not do anything with it.  Trying to view it I received an error saying it could not find the file and when attempting to delete I got an access denied message.  Any help you could provide would be greatly appreciated.

---

### Post by ago on 2007-08-06
> **cspclay said:**
> I cannot get my windows on my host machine to boot after installing wubi to a virtual. 

That has nothing to do with wubi, since wubi does not touch the mbr, particularly when wubi is installed within a VM

---

### Post by cspclay on 2007-08-06
> **ago said:**
> That has nothing to do with wubi, since wubi does not touch the mbr, particularly when wubi is installed within a VM
That is kind of what I thought, but that is the only thing that has changed.  I didn't think it would have anything to do with it either but my errors I get when I boot up are with Grub..... last I checked Vista didn't use Grub for aynthing.  Only thing remotely close to needing Grub was Wubi....which I installed in a VM.

---

### Post by azagorath on 2007-08-08
try to use the last updated version of grub4dos :guitar:

---

### Post by hh93 on 2007-08-29
> **cspclay said:**
> I installed wubi to a virtual machine using MS VPC.  I shut it down instead of rebooting when finished with the installation.  I ran some updates on my host computer and rebooted it when finished and I received a grub error screen saying it could not find the option for Windows Vista and kernel was not compiled to load ubuntu so it took me straight to command line.  I cannot get my windows on my host machine to boot after installing wubi to a virtual.  Not quite sure what to do from here.  I booted to recovery console and ran chkdsk and even tried a system restore to no avail.  To run the system restore I had to run it "offline" because the windows recovery console did not recognize my windows installation anymore.  I noticed on my root drive a grldr file but could not do anything with it.  Trying to view it I received an error saying it could not find the file and when attempting to delete I got an access denied message.  Any help you could provide would be greatly appreciated.

Anything with extension .mbr in c:\ ?

---

