---
title: "Linux md  number is changing - bug ?"
date: 2020-10-13
forum: General Help
---

### Post by helen314 on 2020-10-13
I can create multiple device - md - using mdadm. 
As an example  md0 
When I check it - using gparted - the number I had assigned changes to usually somewhere near maximum allowable ( 127?) 
such as "md122" . Seems as random numbering - downwards from 127. 
Makes it hard to implement auto-mount on boot.  
I am using 16.04.7 for now.

---

### Post by TheFu on 2020-10-13
Use the UUID instead or put an LVM PV+VG+LV onto that array and mount using those.

My 16.04 RAID box ... mdadm devices haven't changed in years. Does the /etc/mdadm/mdadm.conf have your arrays defined? Inside mine, the UUID for each was set. I suppose that happened during the mdadm assemble or create steps.  It has been since 10.04, when these were setup. They've never changed device names.

Check the /etc/mdadm/mdadm.conf file.

---

### Post by helen314 on 2020-10-13
My post is about  system changing md number I have assigned using mdadm --create. 
Obviously it show up during creation of new RAID. 

I have had similar issues with 16.04.6. 

I am not aware that you can do mdamd --create  using UUID. 


Some day I will put together a document showing relations  of various Linunx files / methods / procedures reating to building / implementing / configure RAID.

As far as I can tell 

 /etc/mdadm/mdadm.conf  does not event give a hit it is related to md numbers assignment. 

```

a@a-SATA:~$ sudo cat  /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Sun, 11 Oct 2020 18:38:00 -0500
# by mkconf $Id$
a@a-SATA:~$ 



```

---

### Post by TheFu on 2020-10-13
```
ARRAY /dev/md/1 metadata=1.2 UUID=[COLOR="#FF0000"]ac416c61:885ec692:5dc9a72b:2a70a601[/COLOR] name=ubuntu:1
ARRAY /dev/md2 UUID=08ef65fd:9c02d85a:ea0c067b:86e1af4c
```
are lines in my /etc/mdadm/mdadm.conf.

I've not seen either devices change.  Are the underlying devices changing? Are any USB connected? I don't use USB devices in RAID, ever.  These are infiniband connected between the external array and the SATA controller on the addin JBOD card.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.7 LTS
Release:        16.04
Codename:       xenial

```

Aren't UUIDs tied to the file system? Not to the array. 
```
$ blkid |grep md
/dev/md1: UUID="[COLOR="#00FF00"]718ff044-d1d8-4bb1-9e56-5b1e1c711bc5[/COLOR]" TYPE="ext4"
/dev/md2: UUID="eec33187-943a-4dbf-b695-a613b1095ae2" TYPE="ext4"
```
Do you have a file system on those devices?  Should be mounting the File system UUID, not the 

My fstab has:
```
# /dev/md1              1.8T  849G  883G  50% /raid
UUID=[COLOR="#00FF00"]718ff044-d1d8-4bb1-9e56-5b1e1c711bc5[/COLOR]    /raid      ext4 defaults 0 2
```

I used colors to show the same values.

---

### Post by helen314 on 2020-10-13
Appreciate all comments, however, I don't get that far implementing my RAID. 
I basically loose control of the process AFTER the array is created. 

Here is much simplified "tutorial" on how I implement RAID(5) on Ubuntu 

```

  	 	 	 	   [h=1]Implementing RAID5[/h] [h=2]Build dev partitions[/h] [h=3]Using gparted  build 3 partitions of same size ( 100GB )[/h] [h=4]Set partition flag to &#8220;raid&#8221;[/h]
Create RAID5  array   
[h=3]Using mdadm[/h] sudo mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc[h=2]Build dev/md0 partition[/h] [h=3]Access  gparted  and verify /dev/md0 is detected  (partition )[/h] [h=4]Build partition table (gpt) 
Build md0 partition 
Set partition flag to &#8220;raid&#8221;  (necessary ?)[/h]Verify md0 
a@a-SATA:~$ blkid | grep md0
?? no md0 

Verify all md

a@a-SATA:~$ blkid | grep md
/dev/md126p1: LABEL="DOC_COPY_LABEL" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTLABEL="DOC_COPY_NAME" PARTUUID="89d19be5-0231-48eb-bcd3-7166fa20e87e"
/dev/md126p2: LABEL="DEV_COPY_LABEL" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTLABEL="DEV_COPY_NAME" PARTUUID="fa4989d7-9a3e-4adb-8f79-e7f05d87aadb"
/dev/md126p3: LABEL="MISC_COPY_LABEL" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTLABEL="MISC_COPY_NAME" PARTUUID="9fb50f6f-f9a9-4be8-a561-31ea2fc72fde"
/dev/md126p4: LABEL="BACK_COPY_LABEL" UUID="a1a4ce77-11ca-439c-ac63-a897e5d2896b" TYPE="ext4" PARTLABEL="BACK_COPY_NAME" PARTUUID="4f7020c4-0375-4132-9498-201df6ac6006"
/dev/md125p1: LABEL="NEW_MD_00" UUID="04893c76-3018-4414-90af-bbd15646e1e8" TYPE="ext4" PARTLABEL="NEW_MD_00" PARTUUID="2f38c6f7-0079-48aa-b40a-b91cd3e26a9a"
/dev/md124p1: LABEL="BACK_MD3" UUID="d2af4a0a-ecaa-48bc-a80c-5dae8b20e5af" TYPE="ext4" PARTLABEL="BACK_MD3" PARTUUID="aab196a9-b06c-4ecc-a5a6-69f0908a4954"
/dev/md124p3: LABEL="DEV_MD3" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTLABEL="DEV_MD3" PARTUUID="d053ce77-69c3-49f0-b5b7-b33016a82793"
/dev/md124p5: LABEL="DOC_MD3" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTLABEL="DOC_MD3" PARTUUID="92fe3bcd-193a-493d-845f-32579b40aa85"
/dev/md124p8: LABEL="MISC_COPY_MD3" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTLABEL="MISC_COPY_MD3" PARTUUID="123d8216-6aff-4c16-8c44-8222007d1809"
/dev/md122p1: LABEL="ECLIPSE_BACKUP" UUID="92f91148-a6dd-4d06-9276-83ba2e39ec07" TYPE="ext4" PARTUUID="6a551d9f-01"
/dev/md122p2: LABEL="DEV_MD2" UUID="506d7ca6-b09c-415b-a681-f7f71ec62513" TYPE="ext4" PARTUUID="6a551d9f-02"
/dev/md122p3: LABEL="MISC_MD2" UUID="922f42e6-6ab1-4cd0-bc82-2aee9868187f" TYPE="ext4" PARTUUID="6a551d9f-03"
/dev/md122p4: LABEL="BACK_TEMP_MD2" UUID="d2af4a0a-ecaa-48bc-a80c-5dae8b20e5af" TYPE="ext4" PARTUUID="6a551d9f-04"
a@a-SATA:~$ 

```

[B]THE PROBLEM
there is no md0 device ![/B]

WHY?

---

### Post by TheFu on 2020-10-13
Those steps don't look correct. Also, appears like there is confusion between a disk device and a partition. Can't look for a tutorial now. sorry.
 
Please post using code-tags, not quote-tags. advanced editor (#) button.

---

### Post by helen314 on 2020-10-14
I am NOT posting code , just messages - those have no reason to  be "cut and paste", code does.
Let's not get involved in form, just help fix the issue - shall we?

It appears that without correct entry (UUID etc...) in fstab the "system" picks md number.
(I find "mount -a" o be very helpful to verify validity of fstab) 
It is also unclear WHAT is correct entry in fstab as far as RAID goes. 
It has been not been verified that the labeled entries have to be in sequence. 
This is not easy to troubleshoot because frequent reboot is required. 

What its worth - yesterday I ended up with CORRECT designation on my test md as zero.

TODAY it is "md1" ! (auto-mounts on boot and works as expected )

It also looks as "gparted" MAY be the app assigning wrong md numbers. 
Using "mdadm"  gives more consistent results.

---

### Post by CelticWarrior on 2020-10-14
> [COLOR=#000000]I am NOT posting code , just messages - those have no reason to be "cut and paste", code does.[/COLOR]


Messages, error messages and all, SHOULD be posted as CODE in order to preserve format. Help others help you by NOT complicating things that are simple and part of online forums etiquette.

---

### Post by QIII on 2020-10-14
Please use code tags to enclose ALL terminal commands and their results, as that is the expected presentation and it makes helping you easier.  Bucking the Forum norms will eventually gain you a reputation for intransigence and others will stop caring to help you -- or worse.

Note that a Forum Moderator has already made the edits for you.

I previously asked you to read the Ubuntu Forums Rules and the Posting Guidelines.  Please do so now.

---

