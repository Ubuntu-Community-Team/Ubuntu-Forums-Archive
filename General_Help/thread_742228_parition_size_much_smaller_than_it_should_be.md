---
title: "parition size much smaller than it should be"
date: 2008-04-01
forum: General Help
---

### Post by broth420 on 2008-04-01
I have installed Ubuntu 7.10 server 64bit on a new 5.25TB server.  I created my partition table like this.  It using a RAID 5 array with a Dell Perc6/i raid controller
swap 8GB
/ 64GB (ext3)
/var 16GB (ext3)
/samba the rest of the drive (XFS)


I just ran out of space onthe samba partition at 708GB.  It should be close to 4.75TB.  what did I do wrong?

I used the server install disc to install the partition table.

---

### Post by broth420 on 2008-04-01
Ok, so I think I figured out the problem, but I have no idea how to fix it.  When I create the last 4.5+TB partition, it only let's me have 708GB of space in it.  What I am trying to do is create the build without setting up that last parititon.

Is there anyone that can tell me how or point me to a tutorial to create the large partition after the install, add the xfs file system, and then add it into the fstab for mounting at boot?

---

