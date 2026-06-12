---
title: "Moving /usr AND /home to a new single partition"
date: 2008-04-19
forum: General Help
---

### Post by chris-man on 2008-04-19
Hello,

I've been googling and searching the forums but cannot find a way to move my /usr and /home directories to a new partition (instead of having a partition for each directory)

Surely you can have say /dev/sda4 with both /usr and /home on it .. ?

Any help is appreciated - cheers!

---

### Post by arizonagroovejet on 2008-04-19
The only way I can think of doing it is using symbolic links. You can't mount the partition at more than one mount point and you can't mount it as /home or at /usr if it contains both so you'd have to mount it somewhere else than create links to directories on it. I think the following would work, but try at your own risk and back up and all that.

- Boot from a Live CD.

- Mount the new partition, and whatever partitions are necessary to see your current /home  /usr /etc and /

- On the new partition create directories called usr and home.

- copy contents of /usr in to the /usr directory on the new partition and similarly for home

-  Edit the /etc/fstab file and put in a mount point for the new partition. Call it /homeusr or something. Remove any mount points for /home and /usr that are in there if you currently have them on their own partitions.

- Rename, or if have a backup you're sure of, delete, the current /home and /usr directories.

- In their place create symbolic links to /home and /usr on the new partition. E..g

$ cd /where_ever_you_mounted_your_current_root_partition
$ ln -s /homeusr/home home 

repeat for usr

- Reboot.

---

### Post by bodhi.zazen on 2008-04-19
I am not sure why you are wanting to do this, why not use a separate partition for each ?

FYI , you can mount a partition in more then one location with mount --bind

So you may need to write a script to mount the partition at boot time, mount it first at /usr then mount --bind it to /home. Watch the options for a home partition ...

mount --bind /usr /home -o nodev,nosuid

Not sure if it will work ???

---

### Post by arizonagroovejet on 2008-04-19
> **bodhi.zazen said:**
> 
FYI , you can mount a partition in more then one location with mount --bind


Oh yeah, forgot about that. But it doesn't really make sense to do it in this case. Least I can't see that it does. You'd have to have the contents of /home and /usr mixed up in the same directory, which could be a bit confusing and seems messy.

Hmmmm. It seems like one of those, yes you can do that and there's at least two ways in which to do it, but are you sure you really want to, things.

---

### Post by bodhi.zazen on 2008-04-19
> **arizonagroovejet said:**
> Oh yeah, forgot about that. But it doesn't really make sense to do it in this case. Least I can't see that it does. You'd have to have the contents of /home and /usr mixed up in the same directory, which could be a bit confusing and seems messy.

Hmmmm. It seems like one of those, yes you can do that and there's at least two ways in which to do it, but are you sure you really want to, things.

LOL, I agree.

It may work as /home is typically a number of directories and thus separate from the things in /usr. After all with a default install they are both in / :rolleyes:

But, indeed, why ?

---

### Post by chris-man on 2008-04-19
Firstly, thank you to everyone who posted!

To arizonagroovejet, many thanks for the mini-guide.
I suspected it would be something along those lines.

To bodhi.zazen, I did consider this too but figured it could get complicated.

I only wanted to do this as it seemed a bit like overkill to have a new partition for each directory you wanted on a disk other than /dev/sda1 (or wherever your OS is installed)

Also the benefit of mounting both directories (or more) on one partition would be that you could resize a single partition to provide more space for both directories.

You see at the moment I'm not sure how big my /usr and /home directories will be (as I'm constantly installing and uninstalling software for instance), so I thought it be easier to simply create one 20 gig partition and stick both directories there.

Anyway.... cheers again to everyone for the quick replies. I guess I'll create two partitions and just get on with it.

---

