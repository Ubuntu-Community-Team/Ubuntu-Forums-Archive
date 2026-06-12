---
title: "how to mount 2 partitions to 1 directory"
date: 2021-06-09
forum: General Help
---

### Post by wangkingqq on 2021-06-09
the current partition mounted to the directory i install software is overloaded, so I mounted another partition to have more space, however is there any means by which I can mount thoes 2 partitions to the same directory, so new softwares can be installed into the new partition while the software installed to the older partition is still accessible.
Thank you very much.

---

### Post by grahammechanical on 2021-06-09
How are you mounting these partitions?

I have several partitions on two hard drives. When I use the file manager to access any partition it gets mounted in the /media/username/ directory. I have also edited the /etc/fstab text file to automatically mount a partition called Data that I keep most of my documents on. That is mounted in the /media/ directory. I understand that when editing fstab to automount partitions it is standard practice to have them mounted in either /media/ or /mnt/.

What method are you using?

Regards

---

### Post by SeijiSensei on 2021-06-09
You could mount the new drive at a temporary mount point like /mnt, then copy over the contents of /usr directory. After doing so, unmount the device, and add an entry in /etc/fstab to mount it as /usr.  /usr/bin contains most of the installed programs.

If everything works correctly, unmount the device, then delete the contents of the original /usr directory to get back all that space.

---

### Post by wangkingqq on 2021-06-09
> **SeijiSensei said:**
> You could mount the new drive at a temporary mount point like /mnt, then copy over the contents of /usr directory. After doing so, unmount the device, and add an entry in /etc/fstab to mount it as /usr.  /usr/bin contains most of the installed programs.

If everything works correctly, unmount the device, then delete the contents of the original /usr directory to get back all that space.
Thank you, sounds a little bit scary... I will try. Thank you

---

### Post by wangkingqq on 2021-06-09
by editing /etc/fstab

---

### Post by ajgreeny on 2021-06-09
You can certainly mount two partitions in the same directory, eg **/mnt** or **/media/<username>** but each partition will be in a separate sub-directory.

You can not mount more than one device/volume in any one folder; if you do so the one mounted first will disappear when the second one is mounted.  This does not mean that the files and folders on that device have been deleted, merely that the mount has been removed in order to mount the second device.

---

### Post by QIII on 2021-06-09
Moved to General Help.  This is a request for assistance, not a chat.

---

### Post by Impavidus on 2021-06-09
You cannot mount 2 filesystems at the same location. You could mount 2 filesystems (present on your 2 partitions) on 2 directories side-by-side, 2 subdirectories in the same directory you use for your software. You could also use LVM to create a logical volume spanning 2 physical volumes, so you can have a single filesystem spanning both partitions. This has important disadvantages: it's harder to manage, fewer people know about it and if one of the hard drives breaks down, you lose the files on both (assuming your partitions are on different drives). If your partitions are on the same drive, it may be better to repartition.

I'm wondering, what makes your partition with software full? Most applications are pretty small and installed by the package manager on the root partition. Are you manually installing a lot of stuff? Even for large applications, it's not the executable file that's big, but a set of supporting data files. They get usually stored in /usr/share. For manually installed stuff, it's just wherever you put it. Applications that use a lot of data files usually have some means to put it in some alternative directory. Sometimes you can specify an alternative data directory in a config file or just use a symlink.

---

### Post by TheFu on 2021-06-09
There are lots of ways to merge 2 partitions into a a single file system.  The most used and most tested would be by using LVM, as Impavidus says above.

LVM requires starting fresh and there are risks when 2 separate devices are merged into a single file system.  I did this with 3 partition about 20 yrs ago and when 2 HDD failed, all the data on all three of the HDDs was lost.  I didn't have backup religion back then. Never recovered any of those files.  If you want to go in this direction, start by setting up LVM on 1 of the disks (call it "B"), create a partition, then a PV, then a VG, then an LV on that same disk. Put a file system onto the LV, then mount it.
Now move/copy all the files from partition "A" to LV "B".  Umount "A" and mount "B" where "A" was.  No wipe partition "A" - put a PV onto it and add that PV to the VG from disk "B".  Now that your Disks A and B are sharing the same VG, you can **lvextend** the LV "B" to include as much of the VG that sits on A and B as you like.  When ever using lvextend, be certain to use the -r switch, which will resize the file system at the same time that the LV is resized larger.

The real power from using LVM is NOT allocating all the storage up front.  Only set the LV size to be what you need for the next 2-3 months, that way you can create snapshots for all sorts of handy reasons - like before doing a patches or backups, and if anything goes wrong, you can revert all the changes to that instant of time that the snapshot was created.  When you are certain all is well, say 1-2 days later, then remove the snapshot and let the disk keep moving forward with the changes.  Best to read up on how LVM snapshots work before using them, since they do freeze blocks of storage which uses storage space as all the modified and new files are written.

There are lots of tutorials about using LVM.

Some other tools that can do this are btrfs and ZFS. Those have some amazing capabilities, though btrfs has had some serious data loss issues over the years and there are warnings against using it for any virtual machines.

Then there are tools like **unionfs** that I have no experience using.  Generally, this class of solution is used for people with media centers who think having many drives appear as 1 is a requirement, which it isn't.  Media center software today easily accepts multiple storage locations for each library under management. I think there must be about 5 different tools similar to unionfs.  To find some alternatives, google "unionfs vs".  These are all slow, BTW, unlike LVM, which is enterprise fast.

A poorman's solution to more storage is to use _symbolic links_, also as Impavidus says above.  I've used this over the decades for many different reasons.  Libvirt can use huge amounts of storage. By default, it puts a new virtual machine virtual HDD into /var/lib/libvirt/images (or close to that).  Each VM can be 1G - 100G in size, but I usually have them about 10G each.  With 15 VMs, that would be 150G of storage in /var/.  Typically, /var/ wouldn't need to be over 2G historically as only log files and apt caches are stored there. Anyways, I've placed VMs onto other storage, mounted under /opt/ somewhere, then created a symlink to the new storage location from  /var/lib/libvirt/images just so I didn't have to figure out and modify all the VM settings for alternative storage for the virtual HDDs.  Symlinks work across different disk/partition devices.  Hardlinks do not.

---

### Post by HermanAB on 2021-06-10
Note that you can make an array of disks a.k.a. JBOD using LVM or mergerfs.  That way it would be possible to effectively mount multiple disks on one mount point.  Some googling will get you going.

---

