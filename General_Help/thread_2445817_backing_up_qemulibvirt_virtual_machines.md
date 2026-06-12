---
title: "backing up qemu/libvirt virtual machines?"
date: 2020-06-19
forum: General Help
---

### Post by jsbiff on 2020-06-19
Hello,

   I've googled this, but the instructions I've found covered just backing up individual virtual machines by doing things like backing up the virtual hard drive and using virsh dumpxml to create an xml for the vm settings.

What I wonder about is backing up the qemu/libvirt *system* - all virtual machines, all snapshots, all settings - for later restore.

Is it sufficient to backup (and then later restore) the entire /var/lib/libvirt directory, and then restore it after doing, e.g. a clean install of Ubuntu + kvm? Or is there other related configs/settings stored in other directories?

---

### Post by TheFu on 2020-06-20
No. You need /etc/ and the list of packages too.  But really, backing up huge blobs is crazy wasteful and takes way too much time.  How to backup VMs depends on the backend storage used and the capabilities of that storage. libvirt supports 20 different storage backends. Which are you using?  Each has pros/cons. What works best would depend on your other available infrastructure. Do you use encryption? If so, at which layer?  Do you use a volume manager inside, outside or both inside and outside the VMs? Is the storage on a NAS or SAN?  Is the storage replicated using ceph or sheepdog or something else?

I used to do the blob backup until the 2 hrs I had for backup window nightly couldn't get more than 1 VM. A better solution was needed.  I switched to rdiff-backup and treated each VM like a physical machine.  Backups take between 20 seconds and 7 minutes per VM now with a few that have 500K files requiring longer.  If you use ZFS, which I never have for VMs, then snapshots and zsend can be used.

I've posted here many times about backups and restore techniques.  
A Script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)
Restoring: [https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
aljames2 script: [https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882](https://ubuntuforums.org/showthread.php?t=2436798&p=13932882#post13932882)
Backup versioing: [https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233](https://ubuntuforums.org/showthread.php?t=2422831&p=13935233#post13935233)

Different systems need different protection levels. Some need 180+ days of backup sets due to being high risk systems. Fortunately, those tend to have relatively small data requirements. Desktops probably need 30-90 days of versions, depending on storage and time.  When another version only takes 5 minutes and 150MB more storage, how many days/versions would you keep?

Of course, backups that have never been validated as being restored are just hope. Until you actually restore following the restore plan, nobody knows if the backups have everything you need or not.  The goal is to have what is necessary to restore, but very little more, especially if that extra stuff uses lots of storage.

---

