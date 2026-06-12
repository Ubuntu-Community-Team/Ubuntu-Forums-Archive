---
title: "fstrim-all will make writing log hung"
date: 2016-11-10
forum: General Help
---

### Post by hobbytp on 2016-11-10
Hi,
    when I execute the /sbin/fstrim-all (we modified it, otherwise the IO hung will be several minutes)
my simple script (only write 0 to a file) will hung 3~4 sec after each ~5 seconds.
The fstrim-all is modfied by us to use ionice to use idle(3) priority, and we change the lengh to 5G or less (5M) but the hung interval is the same.
I use "sar -p -d 1 1000" to monitor the IO, and find when the script is hung, the "wr_sec/s" will be huge (e.g. [COLOR=#ff0000]**67110760**[/COLOR].00 )
The sar output, my simple script and modified fstrim-all is as below, I run my simple script in VM which running in this host, it also hung in same interval and my application will be crashed for this issue. I doubt it is ubuntu issue, so any comment and support is highly appreciated. The ubunto verstion is:
# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    **Ubuntu 14.04.5 LTS**
Release:        14.04
Codename:       trusty


+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
**the sar -p -d 1 100 output:**
10:50:15 AM       DEV       tps  rd_sec/s  wr_sec/s  avgrq-sz  avgqu-sz     await     svctm     %util
10:50:16 AM       sda     65.00      0.00    104.00      1.60      0.00      0.00      0.00      0.00
10:50:16 AM       sdb    258.00      0.00 8390191.00  32520.12      3.50      1.18      1.74     44.80
10:50:16 AM       sdc     98.00      0.00    344.00      3.51      0.00      0.00      0.00      0.00
10:50:16 AM       sdd      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
10:50:16 AM   vm-nova    275.00      0.00 **67110760**.00 244039.13      3.50      1.11      1.63     44.80
10:50:16 AM  logs-log      0.00      0.00      0.00      0.00      0.00      0.00      0.00      0.00
10:50:16 AM   os-root     12.00      0.00     96.00      8.00      0.00      0.00      0.00      0.00



**Updated fstrim-all and my small script.**
is as below, 
I highligh the modified by **[COLOR=#ff0000]RED[/COLOR]**

#-------------***fstrim-all***----------
#!/bin/bash
#
# Call fstrim on mounted partitions to maintain write performance.
# This is only relevant for SSD drives, see
# [http://wiki.ubuntuusers.de/SSD/TRIM](http://wiki.ubuntuusers.de/SSD/TRIM)
set -e


# needs /proc
[ -r /proc/mounts ] || exit 0


# these file systems support trimming
SUPPORTED_FS="ext3 ext4 xfs btrfs"


# arguments: <haystack> <needle>
contains() {
    [ "${1#*$2}" != "$1" ]
}


[COLOR=#ff0000]fstrim_ranged() {[/COLOR]
[COLOR=#ff0000]    local mount=$1[/COLOR]
[COLOR=#ff0000]    local fs_total_size_in_bytes[/COLOR]
[COLOR=#ff0000]    local length=$((1024*1024*1024*5)) **#length of bytes to discard in one run (set to 5GB), I also try **[/COLOR]**[COLOR=#FF0000]1024*1024*500 or [/COLOR][COLOR=#FF0000]1024*512,but the hung is the same[/COLOR]**
[COLOR=#ff0000]    while read -r fs_name fs_total_size_in_bytes rest; do[/COLOR]
[COLOR=#ff0000]        for offset in `seq 0 $length $(($fs_total_size_in_bytes-$length))`; do[/COLOR]
[COLOR=#ff0000]            ionice -c 3 fstrim -vo $offset -l $length $mount     **# we use ionice to set to idle level(3)**[/COLOR]
[COLOR=#ff0000]            sleep 5[/COLOR]
[COLOR=#ff0000]        done[/COLOR]
[COLOR=#ff0000]    done < <(df -B1 $mount | grep $mount)[/COLOR]
[COLOR=#ff0000]}[/COLOR]


# As long as there are bugs like [https://launchpad.net/bugs/1259829](https://launchpad.net/bugs/1259829) we only run
# fstrim on Intel and Samsung drives; with --no-model-check it will run on all
# drives instead.
if [ "$1" = "--no-model-check" ]; then
    NO_MODEL_CHECK=1
fi


DONE=''
while read DEV MOUNT FSTYPE OPTIONS REST; do
    # only consider /dev/*
    [ "${DEV#/dev}" != "$DEV" ] || continue
    # ignore mounts with "discard", they TRIM already
    if contains "$OPTIONS" discard; then continue; fi
    # only consider supported file systems
    if ! contains "$SUPPORTED_FS" "$FSTYPE"; then continue; fi
    # ignore temporary devices which already went away
    [ -e "$DEV" ] || continue


    # did we see this already? we need to resolve symlinks
    # for/dev/disks/by-{label,uuid}, etc.; ignore if the device does not exist
    # any more
    REALDEV=`readlink -f $DEV` || continue
    if contains "$DONE" " $REALDEV "; then continue; fi
    DONE="$DONE $REALDEV "


    #echo "device $DEV real $REALDEV mountpoint $MOUNT fstype $FSTYPE"


    # check if that device supports trim; this does not work for devmapper or
    # mdadm, though, so just call fstrim on those without the extra check and
    # ignore errors; for cryptsetup and LVM you also need extra configuration
    # options to propagate discards, which the admin might have turned off
    unset SILENT_FAILURE
    if [ "${REALDEV#/dev/dm-}" != "$REALDEV" ]; then
        #echo "device $DEV is on devmapper, skipping TRIM feature check"
        SILENT_FAILURE=1
    elif [ "${REALDEV#/dev/md}" != "$REALDEV" ]; then
        #echo "device $DEV is on mdadm, skipping TRIM feature check"
        SILENT_FAILURE=1
    elif ! type hdparm >/dev/null 2>&1; then
        #echo "hdparm not available, cannot TRIM"
        exit 0
    else
        HDPARM="`hdparm -I $REALDEV 2>/dev/null`" || continue
        if [ -z "$NO_MODEL_CHECK" ]; then
            if ! contains "$HDPARM" "Intel" && \
               ! contains "$HDPARM" "INTEL" && \
               ! contains "$HDPARM" "Samsung" && \
               ! contains "$HDPARM" "SAMSUNG" && \
               ! contains "$HDPARM" "OCZ" && \
               ! contains "$HDPARM" "SanDisk" && \
               ! contains "$HDPARM" "Patriot"; then
                #echo "device $DEV is not a drive that is known-safe for trimming"
                continue
            fi
        fi
        if ! contains "$HDPARM" "TRIM"; then
            #echo "device $DEV does not support trimming"
            continue
        fi
    fi


[COLOR=#ff0000]    if [ -n "$SILENT_FAILURE" ]; then[/COLOR]
[COLOR=#ff0000]        fstrim_ranged $MOUNT 2>/dev/null || true[/COLOR]
[COLOR=#ff0000]    else[/COLOR]
[COLOR=#ff0000]        fstrim_ranged $MOUNT[/COLOR]
[COLOR=#ff0000]    fi[/COLOR]
done < /proc/mounts

*#-------------**my small script**----------*

[COLOR=#333333][FONT=Arial]while [ 0 ];do[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]echo "0" | tee /var/lib/nova/t.txt[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]sleep 0.001[/FONT][/COLOR]
[COLOR=#333333][FONT=Arial]done

[/FONT][/COLOR]

**The partition info:**
root@compute-0-10:~# lsblk
NAME                MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                   8:0    0 372.6G  0 disk 
&#37433;&#28350;&#25890;sda1                8:1    0    24M  0 part 
&#37433;&#28350;&#25890;sda2                8:2    0   200M  0 part 
&#37433;&#28350;&#25890;sda3                8:3    0   200M  0 part /boot
&#37433;&#28350;&#25890;sda4                8:4    0  50.1G  0 part 
&#37433;&#37433;&#26042;&#25890;os-root (dm-2)  252:2    0    50G  0 lvm  /
&#37433;&#28350;&#25890;sda5                8:5    0  40.1G  0 part 
&#37433;&#37433;&#26042;&#25890;logs-log (dm-1) 252:1    0    40G  0 lvm  /var/log
&#37433;&#28350;&#25890;sda6                8:6    0   282G  0 part 
&#37433;&#37433;&#26042;&#25890;vm-nova (dm-0)  252:0    0     1T  0 lvm  /var/lib/nova
&#37433;&#26042;&#25890;sda7                8:7    0    20M  0 part 
sdb                   8:16   0 372.6G  0 disk 
&#37433;&#28350;&#25890;sdb1                8:17   0    24M  0 part 
&#37433;&#28350;&#25890;sdb2                8:18   0   200M  0 part 
&#37433;&#26042;&#25890;sdb3                8:19   0   372G  0 part 
  &#37433;&#26042;&#25890;vm-nova (dm-0)  252:0    0     1T  0 lvm  /var/lib/nova
sdc                   8:32   0 372.6G  0 disk 
&#37433;&#28350;&#25890;sdc1                8:33   0    24M  0 part 
&#37433;&#28350;&#25890;sdc2                8:34   0   200M  0 part 
&#37433;&#26042;&#25890;sdc3                8:35   0   372G  0 part 
  &#37433;&#26042;&#25890;vm-nova (dm-0)  252:0    0     1T  0 lvm  /var/lib/nova
sdd                   8:48   0   7.5G  0 disk 


root@compute:~# **mount**
/dev/mapper/os-root on / type ext4 (rw,errors=panic)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda3 on /boot type ext2 (rw)
/dev/mapper/logs-log on /var/log type xfs (rw,prjquota)
/dev/mapper/vm-nova on /var/lib/nova type xfs (rw,noatime,nodiratime)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)

**/dev/mapper/vm-nova on /var/lib/nova type xfs (rw,noatime,nodiratime)**


**/etc/fstab**
UUID=f1719b69-8f38-48ab-9c8f-fd1895c69817 /var/lib/nova xfs defaults,noatime,nodiratime 0 0  #I add noatime,nodiratime, but helpless.

I check /sda/sdb/sdc/sdd and all TRIM supported as below
#hdparm -I /dev/sda | grep "TRIM supported"
    Data Set Management **TRIM supported** (limit 6 blocks)


Thanks lots

Hobby

---

### Post by hobbytp on 2016-11-10
My SSD info is:


root@compute-0-10:~# **smartctl -i /dev/sdc**
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-4.4.0-34-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, [www.smartmontools.org](www.smartmontools.org)


=== START OF INFORMATION SECTION ===
Model Family:     Intel DC S3700 Series SSDs
Device Model:     INTEL SSDSC1NA400G3
Serial Number:    BTTV520405B4400BGN
LU WWN Device Id: 5 5cd2e4 04c02d4e9
Firmware Version: 5DV10270
User Capacity:    400,088,457,216 bytes [400 GB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    Solid State Device
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ACS-2 T13/2015-D revision 3
SATA Version is:  SATA 2.6, 6.0 Gb/s (current: 6.0 Gb/s)
Local Time is:    Thu Nov 10 11:47:12 2016 UTC
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

---

