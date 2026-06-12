---
title: "multiple &quot;mounts&quot; on nautilus"
date: 2013-01-01
forum: General Help
---

### Post by then_dude on 2013-01-01
Hello people,

i got myself an old problem, which i always ignored but now i would like to get it out of the way. 

I automount all my partitions on startup. I make use of the UUID in the /etc/fstab file. 

I get all the partitions nicely auto mounted at startup in nautilus, but all the same partitions are displayed twice; and those who are not automounted cannot be mounted... 

I would like that these duplicates are not shown anymore...

i have searched this problem, it was reported as a bug in 2009, but reading through the posts i could not get a decent answer on this problem. 

PS: i want to use the UUID option in the fstab file, this way i can connect other harddisks without messing up my system. (one a week a friend drops by with a broken harddisk asks for restore or saving his documents....)

thanks guys

---

### Post by ctglobal on 2013-01-01
I had a similar problem when I created mount points (using mkdir).

I resolved the issue by removing the directories I created, and making sure the mount point I defined in /etc/fstab matched the drive label e.g. /media/VIDEO, where my hard drive's label was VIDEO. Note that /media/VIDEO does not exist as a directory when the disk is not mounted.

Hope this helps.

---

### Post by Morbius1 on 2013-01-01
There is an unbelievably old bug which I had bookmarked. I went to it to see when it was fixed since it was submitted over 3 years ago and um...
it appears t be still active: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/442130)

To net this out, if you have a line in fstab that looks like this:
> UUID=a-long-number /mount-point .....Change it to this:
> [COLOR=Blue]**/dev/disk/by-uuid/a-long-number**[/COLOR] /mount-point .....

---

### Post by then_dude on 2013-01-01
thanks guys,

 i have altered the fstab file with  "/dev/disk/by-uuid/a-long-number /mount-point ..... " and it worked. but then another question arises


[LIST=1]
[*]with the [COLOR=Blue]**/dev/disk/by-uuid/a-long-number**[/COLOR] /mount-point .....option: if i switch harddisks in my system will it still connect  the "right" harddisk with the "right" mounting point (with this [COLOR=Blue]**/dev/disk/by-uuid/a-long-number**[/COLOR] /mount-point ..... option ?) for example: i disconnect a harddisk put in another and then switch this harddisk for the old one. will it still put the old harddisk on the correct mounting point ? ? It is importent to me cause a lot of applications point to different partitions and harddisk to save the data ??
[*]or can i solve this problem via another way ?
[/LIST]
thanks guys


ps: all the labels were correct and were exactly the same as pointed to.. (so i guess that might be not the problem, or maybe i didn't fully understand your solution to the problem)
thanks

---

### Post by Morbius1 on 2013-01-01
> with the [COLOR=Blue]**/dev/disk/by-uuid/a-long-number**[/COLOR]  /mount-point .....option: if i switch harddisks in my system will it  still connect  the "right" harddisk with the "right" mounting point  (with this [COLOR=Blue]**/dev/disk/by-uuid/a-long-number**[/COLOR] /mount-point ..... option ?)It should since all this is doing is saving the system the step of going to /dev/disk/by-uuid to look it up. And the first "u" in uuid is unique - there can't be more than one disk with that uuid number.

[COLOR=Blue]**EDIT**[/COLOR]: Well, maybe if you clone the disk there might be multiple disks with the same uuid.
[B]
[COLOR=Blue]EDIT2[/COLOR][/B]: If you run the following command I think you can see what /dev/disk/by-uuid is doing:
```
 ls -al /dev/disk/by-uuid
```
They are just a bunch of links pointing to what the /dev/sdxy is at the moment.

---

### Post by dcstar on 2013-01-02
The "problem" only exists because people mount things incorrectly.

/media is a **System Folder** for **exclusive use of the System** for mounting and unmounting removable devices.

**Do not ever put /media mount points in your /etc/fstab file**, use a different mount point like /mnt (or whatever).

---

### Post by Morbius1 on 2013-01-02
> **dcstar said:**
> The "problem" only exists because people mount things incorrectly.

/media is a **System Folder** for **exclusive use of the System** for mounting and unmounting removable devices.

**Do not ever put /media mount points in your /etc/fstab file**, use a different mount point like /mnt (or whatever).
You keep posting this as though it was a statement of fact.

From [http://wiki.debian.org/FilesystemHierarchyStandard:](http://wiki.debian.org/FilesystemHierarchyStandard:)
> /media/ Mount points for removable **media** such as CD-ROMs (appeared in FHS-2.3)
The "system" should stop using /media for internal partitions since they are not removable ( not without a screwdriver ).
> /mnt/ Temporarily **m**ou**nt**ed filesystems

Can't use /mnt in fstab since these internal partitions are no more temporary than the mounting in fstab of the root directory itself.

The only "correct" thing to do is not to mount these non-system partitions at all. Anywho, it makes less sense with the introduction of 12.10 because the "system" moved the mount point from /media/LABEL to /media/$USER/LABEL.

To me it appears to be a case of "failure to communicate". There's 2 different processes taking place. One process wants to create a bookmark for all those partitions not defined in fstab so that the user can mount them through the file manager. The other process is the one that mounts these partitions at boot time if they are defined in fstab. If these two processes don't talk to each other you have a Ruh Row moment. That&#8217;s just a theory on my part but this is a forum so I declare it a "fact".

[COLOR=Blue][I]Also from [http://wiki.debian.org/FilesystemHierarchyStandard](http://wiki.debian.org/FilesystemHierarchyStandard) :
> Still, the vast majority of the Linux distributions, including those  developed by members of the Free Standards Group, do not follow this  proposed standard. In particular, paths specifically created by the FHS  editors, such as /media/ and /srv/, do not see widespread usage.We can't even get all the Linux distros to agree on these standards.[/I][/COLOR]

---

### Post by then_dude on 2013-01-04
so are you saying that since 12.10 the mounting of partitions happens for each user individually? that would be nice (not for me...) 

thanks for the answers. 
ps: can i report that this issue is solved ?

---

### Post by Morbius1 on 2013-01-04
> **then_dude said:**
> so are you saying that since 12.10 the mounting of partitions happens for each user individually? that would be nice (not for me...) 

thanks for the answers. 
ps: can i report that this issue is solved ?
It's turning out to be a real pain in the butt if you want to create a samba share of the thing.

Let's say that you have an internal ext4 partition that you did not automount through fstab or one that is in an external USB device. You set it at 777 permissions so everyone can access it. 

Prior to 12.10: It mounts to /media/LABEL with permissions = 777 and /media itself has permissions = 755 so everything is fine.

12.10: It mounts to /media/morbius/LABEL with permissions = 777 but /media/morbius has these permissions:
> ls -al /media/morbius
drwxr-x---+ 3 root rootRuh Roh. Doesn't look like even morbius is going to get through that. But that "+" at the end means it is using Access Control Lists to determine who has access and it turns out it's only me:
> getfacl /media/morbius
getfacl: Removing leading '/' from absolute path names
# file: media/morbius
# owner: root
# group: root
user::rwx
user:morbius:r-x
group::---
mask::r-x
other::---I can get through to /media/morbius/LABEL but no one else can.

---

