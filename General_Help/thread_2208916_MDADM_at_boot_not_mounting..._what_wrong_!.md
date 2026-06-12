---
title: "MDADM at boot not mounting... what wrong !"
date: 2014-03-03
forum: General Help
---

### Post by jimbohello on 2014-03-03
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=jimbohello group=jimbohello mode=0777 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR [email]jimbohello@publigo.ca[/email]

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=9791cc56:13fe172b:618a7c6a:7c25b737
ARRAY /dev/md/RAID container=9791cc56:13fe172b:618a7c6a:7c25b737 member=0 UUID=d80520d9:e26f2ad9:3f2ef537:2a78cd6a

# This file was auto-generated on Sun, 02 Mar 2014 13:18:44 -0500
# by mkconf $Id$


look like automounting at startu not working ! what<s wrong

---

