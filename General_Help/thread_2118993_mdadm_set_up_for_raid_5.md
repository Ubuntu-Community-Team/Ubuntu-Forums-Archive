---
title: "mdadm set up for raid 5"
date: 2013-02-22
forum: General Help
---

### Post by masterpop on 2013-02-22
Hi,

I have created an array /dev/md0 using 4 x 3TB drives. After a reboot however, the raid device is no longer on /dev/md0. It's still there, and can be mounted, but it's on 

if you run gparted it gives the error that "Could not stat device /dev/md/0"

it seems to get mounted to /dev/md127p1

If I run 
sudo mdadm --detail --scan
it returns: ARRAY /dev/md/HTPC:0 metadata=1.2 name=HTPC:0 UUID=e131543e:18703a09:4b799c90:2fe7673f


which seems wrong to me...

/etc/mdadm/mdadm.conf looks like this:
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
# CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 UUID=e131543e:18703a09:4b799c90:2fe7673f


# This file was auto-generated on Fri, 02 Nov 2012 19:29:38 +0000
# by mkconf $Id$

Would anyone be able to help me so that the drive is mounted correctly? thank you v much for your time

---

