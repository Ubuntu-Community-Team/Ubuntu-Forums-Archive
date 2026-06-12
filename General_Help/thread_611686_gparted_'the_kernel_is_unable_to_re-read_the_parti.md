---
title: "gparted 'the kernel is unable to re-read the partitiontables on the following devices"
date: 2007-11-13
forum: General Help
---

### Post by sporto on 2007-11-13
Dear all,
I have 6 hdds, 2 raid 5 arrays, 1 of which was create by the ubuntu alternate cd before installing ubuntu on it. I have just created the other using the following commands:

sudo mdadm --create /dev/md2 --level=5 --raid-devices=3 /dev/sdd /dev/sde /dev/sdf
sudo mkfs -t ext3 /dev/md2

I also added it to /etc/mdadm/mdadm.conf , this step was necessary to get a uuid in disk-by-uuid which I then added to /etc/fstab.

All seems to be working perfectly but when I launch gparted to look at my disks I get a strange error 'the kernel is unable to re-read the partitiontables on the following devices: - /dev/md1'.

md1 is working properly as sudo mdadm -D /dev/md1 gives state : active and it is the main disk of my ubuntu installation, i.e.  /

md2 is also working fine.. ls /media/windows/
lost+found

(I called it windows as I'll be storing a vmware machine on the array)

any ideas?

Thanks.

---

