---
title: "Problem after installing new drives"
date: 2015-05-12
forum: General Help
---

### Post by david_silvester on 2015-05-12
I have a system running Ubuntu server latest version.

I had two 2tb drives configured as raid 1 using mdadm.

I think I had 3 partitions - swap, boot and data,

I installed 2 4tb drives yesterday, configured as raid 1 using parted.

Now after a reboot the system has not come back up.

The only thing that stands out to me now that I think about it is that when I added the new drives, they appeared as sdb and sdd which seemed strange as I thought they would have been sdc and sdd so I wonder if that is the issue.

Just wondering if anyone has any ideas before I travel to the data centre...?

---

### Post by david_silvester on 2015-05-12
Hi guys,
I have sorted this out now - the raid volume that I created was /dev/md3 and I put a line in fstab to mount it as /backups2
when I got to the DC I realised that it was failing to mount and causing the system to halt on boot up.
On further investigation the volume had changed to /dev/md127
Anyone know why that would have happened?

---

