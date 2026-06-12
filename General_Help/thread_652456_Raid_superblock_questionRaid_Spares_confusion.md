---
title: "Raid superblock question/Raid Spares confusion"
date: 2007-12-28
forum: General Help
---

### Post by John Lentz on 2007-12-28
Hi,

I've been messing with a raid 5 setup a bit and I'm getting confused on some of the parameters I've seen.  I used mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
to create the array and it is running fine.

However, I've seen 2 things that confuse me.  When I run sudo mdadm --detail --scan --verbose, I get:

 sudo mdadm --detail --scan --verbose
ARRAY /dev/md0 level=raid5 num-devices=3 spares=1 UUID=752c40bc:3dbea4cc:64f9287c:8af89c9a
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1

However, I didn't specify any spares.  My /etc/mdadm/mdadm.conf file has an ARRAY line, but it doesn't have a spares parameter on it.  So why does the --detail show a spares=1?

Also, when I run sudo mdadm --examine /dev/md0, I get:
mdadm: No md superblock detected on /dev/md0.

Is that normal for using mdadm to create the array?  Also, does it matter?  I'm new to all of this and I'd appreciate any enlightenment.

Thanks,

John

---

### Post by kidders on 2007-12-30
Hi there,

When dealing with RAID arrays, the more information you can give, the better. Could you post the output of the following...

Summarise volume information for everything in /dev that looks like "hda5", "sda", etc:```
for f in /dev/[sh]d[a-z]*; do echo $f; sudo vol_id $f; done
```

Some information about the state of your RAID array:```
sudo mdadm --detail /dev/md0
```

[SIZE=1][COLOR=Red][ Just FYI, both of these commands run with root privileges, so don't execute them without satisfying yourself they're not malicious. ]
[/COLOR][/SIZE]
Also, have you formatted & mounted your array successfully yet?

---

### Post by John Lentz on 2007-12-30
> **kidders said:**
> Hi there,

When dealing with RAID arrays, the more information you can give, the better. Could you post the output of the following...

Summarise volume information for everything in /dev that looks like "hda5", "sda", etc:```
for f in /dev/[sh]d[a-z]*; do echo $f; sudo vol_id $f; done
```

Some information about the state of your RAID array:```
sudo mdadm --detail /dev/md0
```

[SIZE=1][COLOR=Red][ Just FYI, both of these commands run with root privileges, so don't execute them without satisfying yourself they're not malicious. ]
[/COLOR][/SIZE]
Also, have you formatted & mounted your array successfully yet?

I have formatted and mounted the array.  It seems to be working just fine and I'm accessing/creating folders as I expect to be able to do.  I just have those 2 questions about why it shows me as having spares=1, when I only have 3 drives in the raid and I didn't specify a spare (unless my boot drive,which isn't in the array is seen as a spare?) and why I get the superblock line.  Here is the info you were requesting.  Thank you for any help.

sudo mdadm --detail /dev/md0

/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Dec 24 17:41:33 2007
     Raid Level : raid5
     Array Size : 1953519872 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec 30 09:14:55 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 752c40bc:3dbea4cc:64f9287c:8af89c9a (local to host babylon)
         Events : 0.3242

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1

for f in /dev/[sh]d[a-z]*; do echo $f; sudo vol_id $f; done[

/dev/sda
ID_FS_USAGE=raid
ID_FS_TYPE=promise_fasttrack_raid_member
ID_FS_VERSION=
ID_FS_UUID=
ID_FS_UUID_ENC=
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sda1
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=8789c063-c7cd-42f3-bd82-0b52cb96d5ed
ID_FS_UUID_ENC=8789c063-c7cd-42f3-bd82-0b52cb96d5ed
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sda2
/dev/sda2: unknown volume type
/dev/sda5
ID_FS_USAGE=other
ID_FS_TYPE=swap
ID_FS_VERSION=2
ID_FS_UUID=26da9145-2d3c-4332-88c0-edcce65e30fc
ID_FS_UUID_ENC=26da9145-2d3c-4332-88c0-edcce65e30fc
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sdb
/dev/sdb: unknown volume type
/dev/sdb1
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_UUID_ENC=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sdc
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=49086ba4-4f03-4f8b-9bbb-66c01bb9274c
ID_FS_UUID_ENC=49086ba4-4f03-4f8b-9bbb-66c01bb9274c
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sdc1
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_UUID_ENC=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sdd
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=af0b39ca-dd9a-41b2-bacb-ffb50ff2f269
ID_FS_UUID_ENC=af0b39ca-dd9a-41b2-bacb-ffb50ff2f269
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=
/dev/sdd1
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_UUID_ENC=752c40bc:3dbea4cc:64f9287c:8af89c9a
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

Thank you

---

### Post by kidders on 2007-12-31
Everything in your last post seems perfectly okay ... you have the right number of devices (active & spare), and a healthy RAID superblock. If it weren't for your o/p, there would be no reason to suspect a problem. :confused:

It's been a while since you started this thread ... are you sure mdadm is still giving you weird, inconsistent feedback about your array?

---

### Post by John Lentz on 2007-12-31
It has been awhile. I just ran:

sudo mdadm --detail --scan --verbose

ARRAY /dev/md0 level=raid5 num-devices=3 UUID=752c40bc:3dbea4cc:64f9287c:8af89c9a
   devices=/dev/sdb1,/dev/sdc1,/dev/sdd1
john@babylon:/home$ sudo --examine /dev/md0

And now it isn't showing any spare devices, so that is OK.  Hooray!

I also ran:

sudo mdadm --examine /dev/md0
mdadm: No md superblock detected on /dev/md0.

It is still reporting No md superblock detected.  Is that normal?

Thanks so much.

John

---

### Post by fjgaude on 2007-12-31
It is for me, John. No md superblock detected on ... is normal, AFAIK.

---

### Post by John Lentz on 2008-01-02
Ok, thanks. I guess I won't worry about it anymore and just enjoy.

Thanks again,

John

---

### Post by fjgaude on 2008-01-02
Thank you for hanging in there, and getting software raid working.

Happy New Year!

---

