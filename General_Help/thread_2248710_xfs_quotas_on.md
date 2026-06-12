---
title: "xfs quotas on   /"
date: 2014-10-16
forum: General Help
---

### Post by O9aIevckc0 on 2014-10-16
I have been trying to set quotas on my root filesystem (XFS) but it responds with the error
xfs_quota:cannot set limits: Function not implemented

though i have searched around i have not been able to find a satisfactory solution

the command i have been using is
xfs_quota -x -c 'limit bhard=500m testuser' /

my fstab is as follows

# <file system> <mount point>  <type> <options>      <dump> <pass>
# / was on /dev/sda1 during installation
 UUID=85308189-071d-487d-91b0-bd23db4698a3 /                xfs    usrquota,grpquota 0      1
# /home was on /dev/sda5 during installation
UUID=f90ee091-8998-4532-a18a-11aa2d26eea9 /home         xfs    usrquota,grpquota 0      2
# swap was on /dev/sda6 during installation
UUIOD=deb917ca-0205-4668-b04b-f340fcbda467 none          swap  sw              0       0

---

