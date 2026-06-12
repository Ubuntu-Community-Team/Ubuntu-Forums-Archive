---
title: "Recovery from lvremove/lvrename"
date: 2016-11-02
forum: General Help
---

### Post by Elliot_Berg on 2016-11-02
So, I had a KVM server running Ubuntu 16.04 LTS with a 1TB disk formatted as LVM, with one group and 2 volumes - one for swap, and one with the rest of the space as the root filesystem. I've started adding other disks to the host and setting them up with properly isolated volumes, so it seemed a good idea to move everything out of the default directory in that root volume, dump it in a new volume in that group, shrink the root volume, etc.

I started off by resizing the filesystem on the root volume. Then I lvreduced the root volume. Then made a new volume (let's call it vm_disks), shuffled the data over, and all seemed to be fine. It booted fine, I could mount the vm_disks volume and it had stuff in it. Libvirt didn't like it though - no matter what I did I kept getting permissions errors. The only thing that I could see that was different between this volume, and every other volume that works, was that it was created using a live disk (because I couldn't do it while the root filesystem was mounted).

So I created a temp_vms volume, shuffled a disk image over to that, and tried using that. Still didn't work, so I shuffled the file back, and went to remove the temp_vms volume. But I was half-asleep, and actually removed the vm_disks volume by mistake. So, I panicked a bit, had a Google, and found out about vgcfgrestore - I poked around in /etc/lvm/archive and ran a vgcfgrestore -f $file using the most recent file for that VG, which seemed to have the right modification in it (which I verified by reading the top of the file). I then removed the temp volume, and renamed the real one back to how it should have been before I tried making the temp volume. 

That left me with volumes that looked correct when running an lvdisplay or a pvdisplay -m. But no matter what I do, I can't get it to mount - running fsck/e2fsck suggests using an alternate superblock, but refuses to use any superblock I've tried.

Long story short, I accidentally deleted the volume, recovered it, renamed it back to how it should have been, and now can't use it. I'm also a bit concerned that I may have damaged the underlying data by trying to restore some of the other vgcfgbackup files in a blind panic - I'm hoping that there's enough left underneath to recover *something* though. If the filesystem were mountable and I could salvage some of the VMs then that would be great.

HELP PLEASE!!!!!!

---

### Post by TheFu on 2016-11-03
I'd wipe the disks and start clean using backups.

Almost 15 yrs ago, I lost 80% of my data due to LVM mistakes on my part. Got backup religion then.  I keep backups on non-LVM disks, but make full use of LVM on primary storage.

---

