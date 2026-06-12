---
title: "HD crash..."
date: 2006-12-01
forum: General Help
---

### Post by lennartack on 2006-12-01
A while ago I did something stupid with my HD: when I was installing an OS it said the partition table wasn't supported and the installer could damage the other partitions, but I simply didn't give attention to it. Forunately I was able to restore my data with fsck. I made a backup of it and made a new partition table with new partitions. But now if I boot ubuntu(wich is installed on my other hd) I get an error:
> Log of fsck -C -R -A -a 
Fri Dec  1 08:53:39 2006

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=692b0818-c68f-488b-bdf7-03317c2ea4f8'

/dev/hda5: clean, 114435/18251776 files, 29622979/36493647 blocks (check after next mount)
fsck died with exit status 8

Fri Dec  1 08:53:39 2006
----------------


Can anyone help me with this?

---

### Post by Herman on 2006-12-01
Open a terminal in a workspace. This command, (below), will give a whole list of your partitions and their UUIDs,
  ```
ls /dev/disk/by-uuid/ -alh
``` Just leave that terminal open for now.

Then change to another workspace and open a second terminal and open your /etc/fstab, ```
sudo gedit /etc/fstab
``` Edit your /etc/fstab to agree with the UUID numbers in the first terminal you have open. Don't forget to save the changes. 

That should solve your problem.
Regards, Herman :D

---

### Post by lennartack on 2006-12-01
Thanks, but can't I just replace the UUIDs with /dev/hdxy?

---

