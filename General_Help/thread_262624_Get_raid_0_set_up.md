---
title: "Get raid 0 set up?"
date: 2006-09-21
forum: General Help
---

### Post by daedalusman on 2006-09-21
Well, I have a raid 0 array setup with my hardware raid controller on my mobo. My question is, how do I get this array setup in ubuntu? Right now ubuntu sees them as two separate hard-drives and reports them as 298.09GB, which seems small considering they are 320GB drives? Should I use lvm to set them up and are the reported sizes right? Any help is much appreciated, thanks.

---

### Post by daedalusman on 2006-09-23
bump

---

### Post by Ocxic on 2006-09-23
LVM is the way to go, much simpler then raid to deal with, while getting the same raid0 effect.

as for the reported size of your drives, they will always be a little less then what it say's of the box, my 200GB shows as 180GB because of the coversion. the box goes by 1000kb=1MB were in actuality 1024kb=1MB so there is a slight loss. unfortuantly.

---

### Post by daedalusman on 2006-09-23
Well thanks for the reply. I used the guide in the forums to setup system-config-lvm (a fedora program) and set up my logical volume group with stripping. LVM doesn't allow you to format it in anything other than ext2 or ext3. I want to have it formatted as XFS. Can I just format the drives using the 'disks' utility in the system>administration menu, or do I have to format the logical volume some other way? Thanks for any help.

---

### Post by Ocxic on 2006-09-23
LVM will allows XFS I'm using it right now with no problems, I would suggest forrmating the volume from a terminal,
with "sudo mkfs.xfs"

---

### Post by daedalusman on 2006-09-23
Alright, thanks. I got it all setup and formatted but can I figure out how to mount it so I can use it. Can you help me out there, I want it to mount at boot like my other drives? Thanks again.

---

### Post by Ocxic on 2006-09-24
mount it just like any other drive,

"sudo mount -t fs-type /dev/mapper/lvm /mount/point"
and you can just copy the line for your root/home partition in your fstab and change the device, and mount point to mach your new lvm setup, and make the last 2 numbers on the line 0 (thats zero not an o).

(edit) tip: don't make the mount point in your /home directory I've found this to cause problems.

---

### Post by daedalusman on 2006-09-24
Awesome, thanks. I just got it up and running about a minute ago. Man this is going to be great. Thanks again for all the help.

---

