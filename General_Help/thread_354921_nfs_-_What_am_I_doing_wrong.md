---
title: "nfs - What am I doing wrong?"
date: 2007-02-06
forum: General Help
---

### Post by Rich78 on 2007-02-06
I've followed a few examples to setup nfs and when I go to mount the folder on my client machine I keep getting: 

mount: 192.168.2.5:/share failed, reason given by server: Permission denied

So far I've done the following:

sudo aptitude -P install nfs-kernel-server nfs-common portmap

sudo vi /etc/exports

In exports I put:

/home/share/ 192.168.2.2/24(rw,no_root_squash,async)

*Please note my server address isn't 192.168.2.2 but it is the start of my IP range on my network, the documentation I read suggested the line above would apply the rule to any PC's on the network between 192.168.2.2 - 192.168.2.255*

Then I checked my /etc/default/portmap file which contains:
#OPTIONS="-i 127.0.0.1"

Then I changed /etc/hosts.allow to the following:

portmap: 192.168.2.
lockd: 192.168.2.
rquotad: 192.168.2
mountd: 192.168.2.
statd: 192.168.2.
nfs: 192.168.2.

Then I changed /etc/hosts.deny to:

portmap:ALL
lockd:ALL
mountd:ALL
rquotad:ALL
statd:ALL
nfs:ALL

Then I did the following:

sudo /etc/init.d/nfs-kernel-server restart

Then on the client machine I did the following:

sudo mount 192.168.2.5:/share /mnt/share


Sorry for the long post, can anyone see where I've gone wrong?

Thanks

---

### Post by Rich78 on 2007-02-07
Anyone got any ideas?

---

