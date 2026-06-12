---
title: "FSTAB, MDADM.conf help please"
date: 2013-11-11
forum: General Help
---

### Post by brandonmiller21 on 2013-11-11
Any idea what is up with my mkconf file?

contents of mkconf:
```
#!/bin/sh
#
# mkconf -- outputs valid mdadm.conf contents for the local system
#
# Copyright Â© martin f. krafft <madduck@madduck.net>
# distributed under the terms of the Artistic Licence 2.0
#
set -eu


ME="${0##*/}"
MDADM=/sbin/mdadm
DEBIANCONFIG=/etc/default/mdadm
CONFIG=/etc/mdadm/mdadm.conf


# initialise config variables in case the environment leaks
MAILADDR= DEVICE= CREATE= HOMEHOST= PROGRAM=


test -r $DEBIANCONFIG && . $DEBIANCONFIG


if [ -n "${MDADM_MAILADDR__:-}" ]; then
  # honour MAILADDR from the environment (from postinst)
  MAILADDR="$MDADM_MAILADDR__"
else
  # preserve existing MAILADDR
  MAILADDR="$(sed -ne 's/^MAILADDR //p' $CONFIG 2>/dev/null)" || :
fi


# save existing values as defaults
if [ -r "$CONFIG" ]; then
  DEVICE="$(sed -ne 's/^DEVICE //p' $CONFIG)"
  CREATE="$(sed -ne 's/^CREATE //p' $CONFIG)"
  HOMEHOST="$(sed -ne 's/^HOMEHOST //p' $CONFIG)"
  PROGRAM="$(sed -ne 's/^PROGRAM //p' $CONFIG)"
fi


generate=0
[ "${1:-}" = force-generate ] && rm -f $CONFIG
case "${1:-}" in
  generate|force-generate)
    [ -n "${2:-}" ] && CONFIG=$2
    # only barf if the config file specifies anything else than MAILADDR
    if egrep -qv '^(MAILADDR.*|#.*|)$' $CONFIG 2>/dev/null; then
      echo "E: $ME: $CONFIG already exists." >&2
      exit 255
    fi


    mkdir --parent ${CONFIG%/*}
    exec >$CONFIG
    generate=1
    ;;
esac


cat <<_eof
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#


# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE ${DEVICE:-partitions containers}


# auto-create devices with Debian standard permissions
CREATE ${CREATE:-owner=root group=disk mode=0660 auto=yes}


# automatically tag new arrays as belonging to the local system
HOMEHOST ${HOMEHOST:-<system>}


# instruct the monitoring daemon where to send mail alerts
MAILADDR ${MAILADDR:-root}


_eof


if [ -n "${PROGRAM:-}" ]; then
  cat <<-_eof
        # program to run when mdadm monitor detects potentially interesting events
        PROGRAM ${PROGRAM}


        _eof
fi


error=0
if [ ! -r /proc/mdstat ]; then
  echo W: $ME: MD subsystem is not loaded, thus I cannot scan for arrays. >&2
  error=1
elif [ ! -r /proc/partitions ]; then
  echo W: $ME: /proc/partitions cannot be read, thus I cannot scan for arrays. >&2
  error=2
else
  echo "# definitions of existing MD arrays"
  if ! $MDADM --examine --scan --config=partitions; then
    error=$(($? + 128))
    echo W: $ME: failed to scan for partitions. >&2
    echo "### WARNING: scan failed."
  else
    echo
  fi
fi


if [ $generate -eq 1 ]; then
  cat <<_eof
# This file was auto-generated on $(date -R)
# by mkconf \$Id$
_eof


  mkdir -p /var/lib/mdadm
  md5sum $CONFIG > /var/lib/mdadm/mdadm.conf-generated
fi


exit $error
```

That has me concerned because it looks nothing like anything I've seen anyone else post examples of.


I saw other people getting the md127 issue but I don't know if it's really a problem or just a bug that can be ignored for now.

Thanks for any help! :)

---

### Post by brandonmiller21 on 2013-11-12
I was able to reboot and the RAID array mounted successfully, but I still don't know if mdadm has setup the config correctly...

---

### Post by brandonmiller21 on 2013-11-12
I'm still concerned with my /etc/fstab file...why is the UUID commented out for swap?  Also, do I need the UUID of the RAID volume to be in there?

```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=82483c62-8c1c-4bb6-8177-baccaa24e107 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=ceadd6af-9503-4faa-bf18-43693444dd82 /boot           ext4    defaults        0       2
# /home was on /dev/sda5 during installation
UUID=0e495155-eaa7-4fc3-b66c-9c5fbde68340 /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
#UUID=d9f61be9-aa01-4261-a0ac-3b690508b8cc none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/owncloud-owncloudlv /mnt/owncloud ext3 rw,noatime 0 0

```

---

### Post by SaturnusDJ on 2013-11-13
So what actually is the problem?

If /dev/md127 is appearing, the definitions in /etc/mdadm/mdadm.conf aren't ok or haven't been send to initramfs most times.

---

### Post by brandonmiller21 on 2013-11-13
> **SaturnusDJ said:**
> So what actually is the problem?

If /dev/md127 is appearing, the definitions in /etc/mdadm/mdadm.conf aren't ok or haven't been send to initramfs most times.

I guess they were fixed when I ran 
```
mrblue@Windoge:~$ update-initramfs -u
```

```
mrblue@Windoge:~$ sudo cat /proc/mdstatPersonalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[2] sdb1[0]
      976631296 blocks super 1.2 [2/2] [UU]


unused devices: <none>

```

I've allocated roughly 930GB of space to this volume as you can see here:
```
mrblue@Windoge:~$ sudo mdadm --detail /dev/md0/dev/md0:
        Version : 1.2
  Creation Time : Thu Nov  7 15:13:20 2013
     Raid Level : raid1
     Array Size : 976631296 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976631296 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent


    Update Time : Wed Nov 13 08:41:14 2013
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0


           Name : Windoge:0  (local to host Windoge)
           UUID : bebaa653:5e4468a6:1c153bb1:f5bb56f6
         Events : 55


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       2       8       33        1      active sync   /dev/sdc1

```

BUT, I'm only seeing 886GB of space available.  I think this might be reserved for growth or something, but I've already set aside space for that.  Do you know how I can reclaim the reserved space?
```
mrblue@Windoge:~$ sudo df -hFilesystem                       Size  Used Avail Use% Mounted on
/dev/sda1                         19G  2.9G   15G  17% /
udev                             1.3G  4.0K  1.3G   1% /dev
tmpfs                            505M  384K  505M   1% /run
none                             5.0M     0  5.0M   0% /run/lock
none                             1.3G  4.0K  1.3G   1% /run/shm
/dev/mapper/owncloud-owncloudlv  886G  408M  886G   1% /mnt/owncloud
/dev/sda2                        181M   86M   86M  51% /boot
/dev/sda5                        184G  115M  174G   1% /home
/home/mrblue/.Private            184G  115M  174G   1% /home/mrblue

```

---

### Post by SaturnusDJ on 2013-11-13
Yes correct, most times the md device appears as in the definitions when the initramfs is updated.

Maybe it's reserved space for the super user and/or recovery of files. It's possible to change the size of this. [http://ubuntuforums.org/showthread.php?t=1908739](http://ubuntuforums.org/showthread.php?t=1908739)

---

