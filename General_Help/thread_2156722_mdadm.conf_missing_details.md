---
title: "mdadm.conf missing details?"
date: 2013-06-22
forum: General Help
---

### Post by Headcase_Fargone on 2013-06-22
Someone in the IRC help channel suggested that I backup my mdadm.conf file for a software RAID5 array before upgrading to 12.04.  I looked in /etc/mdadm/mdadm.conf and saw literally no reference to my array mounted as md0.  So I ran a command I found in the wiki for generating this file: mdadm --detail --scan >> /etc/mdadm/mdadm.conf.  My conf files now look like this:

**/etc/mdadm.conf**
> 
ARRAY /dev/md0 metadata=1.2 spares=1 name=MediaNew:0 UUID=c922382d:a8decfb4:0bdbd2de:67332819


**/etc/mdadm/mdadm.conf**
> 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions


# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes


# automatically tag new arrays as belonging to the local system
HOMEHOST <system>


# instruct the monitoring daemon where to send mail alerts
MAILADDR root


# definitions of existing MD arrays


# This file was auto-generated on Sat, 31 Dec 2011 19:00:57 -0600
# by mkconf $Id$
ARRAY /dev/md/0 metadata=1.2 name=MediaNew:0 UUID=e8556bbd:4885837b:be8c7739:408cfb8d


From what I'm seeing of example conf files, there should be entries for each of the drives making up this array.  But I don't see anything like that.

Am I doing something wrong generating this file?

---

### Post by SaturnusDJ on 2013-06-23
The UUID identifies the array members.
Use the mdadm examine command at the members and you'll see the UUID appearing there.

---

