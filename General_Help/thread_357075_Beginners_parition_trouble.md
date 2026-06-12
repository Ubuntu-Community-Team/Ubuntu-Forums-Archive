---
title: "Beginners parition trouble"
date: 2007-02-09
forum: General Help
---

### Post by krixo on 2007-02-09
Hi

When I installed my Ubuntu 6.06 server, I made an extre partition just for future use. 2GB. Now I have come so far, to move my files to the server and discover that the home directory is mounted at the 2GB partition. So how can I get the /home/ back to the root filesystem? (and copy stuff back to the new /home/)

This is how /etc/fstab looks:
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2   /                  ext3    defaults,errors=remount-ro 0       1
/dev/hda3   /home          ext3  suid,dev,usrquota,exec  0  2
/dev/hda1   none            swap    sw              0       0
/dev/hdd     /media/cdrom0   udf,iso9660 user,noauto     0       0

thankyou for reading this far

---

### Post by toGoq on 2007-02-09
Are you sure you want to move your /home patition to the root filesystem?
Perhaps you'd like to read this topic first:
[http://ubuntuforums.org/showthread.php?t=46866&highlight=howto+moving+%2Fhome]("http://ubuntuforums.org/showthread.php?t=46866&highlight=howto+moving+%2Fhome")

As you can see having a separate /home partition has it's advantages, though in your case your home is indeed quite small.

---

### Post by goatflyer on 2007-02-09
I'm not sure why you have all the mount options set for your current home partion on /dev/hda3, but lets ignore that for now.

To answer your question (how to copy home files back to / partition) the easiest way would be if you could boot using a live cd.


Boot live cd.
Get into terminal
create 2 subdirectories like this:
  mkdir /mnt/p2
  mkdir /mnt/p3

mount both partitions
  mount -t ext3 /dev/hda2 /mnt/p2
  mount -t ext3 /dev/hda3 /mnt/p3

confirm for yourself that all your home directories are intact, eg:
  ls /mnt/p3

I don't know how many user accounts you have on your current home partition (maybe only 1?), in any case now examine partition 2

  ls /mnt/p2

(this is your harddisk root).  I'll bet there is already a 'home' directory there.  Lets look at it:

  ls /mnt/p2/home

Now my question is: do you see any user accounts there?  Is your user name there?  If so, lets rename it to something safe for now:

  mv /mnt/p2/home/myname /mnt/p2/home/oldmyname

(replace 'myname' with whatever your user account name is).

The reason we did that is in case it contains any long-lost treasures, you will be able to explore/recover that after we start up with the new home directory.

Now for the actual copying of files (I assume you have enough space on your root partition)

 cp -rpf /mnt/p3/myname /mnt/p2/home

If there was more than one user account, then repeat the above two commands changing the name (i.e. rename the old one, then copy the new).


At this point you effectively have two copies of your home partition.  Nothing has been deleted.

Last step: edit the fstab of the root partition.

 nano /mnt/p2/etc/fstab

Comment out the mount line for /dev/hda3 like this:

# /dev/hda3 /home ext3 suid,dev,usrquota,exec 0 2

The save and exit by hitting ctl-X, then 'y', then press enter.

Unmount everything like this:

umount /dev/hda2
umount /dev/hda3

Exit the terminal, quit the live cd, and restart your system.  You will now be using the /home found on the / partition.

If for some reason you want to undo, just remove the '#' character from the /etc/fstab file and reboot.

After you confirm everything is working fine, you can safely repurpose /dev/hda3

---

### Post by krixo on 2007-02-12
Thanks both of you! That was a big Ubuntu mokka. I see the anvantage of having a seperate home partition, but I went for the simple setup. It all worked and the home dir is now in the root directory.
Regards

---

