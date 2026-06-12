---
title: "vmware: using physical ntfs data partition"
date: 2006-07-31
forum: General Help
---

### Post by RikoW on 2006-07-31
Hi everyone,

I have a dual boot laptop running XP and Ubuntu. XP has two partition one of which is used as a data disk (X:).

I'm also running XP in Ubuntu using vmware. The virtual machine is running entirely within the Linux filesystem. However, I would like to access the data partition of the windows installation (X:) also from the virtual machine. But when I add a physical disk to the virtual, select the correct partition and try to power up the machine, I get an error mesage saying:

> Cannot open the disk '/home/wichmann/vmware/mpyxvriko/mpyxvriko-1.vmdk' or one of the snapshot disks it depends on.
Reason: The partition table on the physical disk has changed since the disk was created. Remove the physical disk from the virtual machine, then add it again.

Following the suggestion of course didn't solve my problem.

When run the virtual machine as root user (needless to say, I don't want to do that!!). The virtual machine starts. So, I assume, it is an access rights problem:

```
> ls -l /dev/hda3
brw-rw---- 1 root disk 3, 3 2006-07-31 11:13 /dev/hda3

```

But, my local user is in the disk group, so should be able to use this disk, right?

Anyone has any ideas, how to set it up correctly, so that I can use a physical partition from a virtual windows machine?

Thanks and cheers,
              Riko

---

### Post by RikoW on 2006-08-03
Ok, so in the end I gave up trying to add the physical ntfs partition to the virtual XP machine. Also on the VMware Workstation forum in didn't find or was offered a solution.

However, I managed to access the partition via shared folder. So in case anybody wants to do something similar, here is what I did:

Remember: I have a dual boot set-up with a physical XP installation an Ubuntu. The physical XP installation has two ntfs drives/partitions C: and X: where X: is a data partition. The drive X: I want to access also in a 2nd XP installations which runs as guest OS in VMware workstation under Ubuntu. Note that the guest XP and the physical XP installation are completely independent.

To access the X: drive from the guest XP in VMware:

1) install ntfs-3g and fuse to enable write access to ntfs under Ubuntu:
 
[INDENT][http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g]("http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g")[/INDENT]

2) to be able to mount the partition also as regular user and not only as root, I added myself to the group "fuse" and set the permissions:

```
> ls -l /usr/bin/fusermount
-rwsr-xr-x 1 root fuse 18344 2006-07-16 16:57 /usr/bin/fusermount*
```

and added to /etc/fstab:

```
/dev/hda3       /windows/x     ntfs-3g silent,noauto,user,locale=en_US.utf8    0    0

```

3) mount the partition (obviously you need to do that everytime before you start your virtual XP)

```
mount /windows/x
```

4) Now you tell your virtual machine to use the above directory as shared folder. In VM workstation click:
        [INDENT]VM -> Settings -> Options -> Shared Folders -> Add[/INDENT]
Browse to /windows/x (or whereever) and give it a name.

5) After powering on your guest XP open an explorer windows click:
        [INDENT]Tools -> Map Network Drive[/INDENT]
   select a drive letter and browse for the folder:
        [INDENT]My Network Places -> Entire Network -> VMware Shared Folders
[/INDENT]
   Here you should find an entry labeled '.\\host' which contains the folders you share on your local machine and select it.

You may want to check the box 'Reconnect on Logon'  in the drive window.


And there you go :)

I hope, somebody finds that useful:)  So far, I'm very happy with the set-up. 


Cheers,

                Riko

---

### Post by matrooswolf on 2006-08-03
Hi Riko,
nice howto!
Btw: Did you read this thread: 
[http://www.ubuntuforums.org/showthread.php?t=183209&page=14&highlight=physical](http://www.ubuntuforums.org/showthread.php?t=183209&page=14&highlight=physical)
User Kurr seems to be able to run his WindowsXP from within vmware (post 131 and following)

---

### Post by RikoW on 2006-08-03
Hi Matrooswolf,

> **matrooswolf said:**
> Hi Riko,
nice howto!


Thanks! :)

> **matrooswolf said:**
> 
Btw: Did you read this thread: 
[http://www.ubuntuforums.org/showthread.php?t=183209&page=14&highlight=physical](http://www.ubuntuforums.org/showthread.php?t=183209&page=14&highlight=physical)
User Kurr seems to be able to run his WindowsXP from within vmware (post 131 and following)

I read part of the thread (here I learned about sharing folders via samba). Only after I had the independent virtual installed, I read about the possibility to boot into the physical install. 
I haven't tried that yet, but if I have some time, maybe I give it a shot to save some diskspace (Maybe tonight, if there is nothing on TV :)

There is actually documentation available from vmware, how to do that properly:

[http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html](http://www.vmware.com/support/ws55/doc/ws_disk_dualboot.html)

That's how I learned it was possible!

Cheers,
               Riko

---

### Post by adeepak on 2006-08-23
I'm using virtual windows XP SP2 inside my ubuntu..
As RikoW said we can use Shared Folders feature of VM ware.. But my problem is that i'm not getting this option in my VMware settings..I'm attaching the screenshots of my virtual machine settings...

---

### Post by RikoW on 2006-08-23
VM Server, which you are using judging from your screen shots, does not seem to support Shared Folders! I'm using VM Workstation, which does support it.

See also this thread on the VM forums:

[http://www.vmware.com/community/thread.jspa?messageID=395381&#395381]("http://www.vmware.com/community/thread.jspa?messageID=395381&#395381")

Cheers,

           Riko

---

