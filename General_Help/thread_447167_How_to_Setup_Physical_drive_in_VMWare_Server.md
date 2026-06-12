---
title: "How to Setup Physical drive in VMWare Server?"
date: 2007-05-17
forum: General Help
---

### Post by Tridion2000 on 2007-05-17
I have Ubuntu Feisty installed and the latest VMWare Server. I have a Windows XP installed as a virtual machine on a 20Gb virtual hard drive. In Ubuntu I also have a 150Gb FAT32 partition which I would like to be able to see in Windows XP. I am trying to add a hard drive in the VMWare settings for this virtual machine.

I select Physical Drive, then "/dev/sda" and then "use individual partitions". The first problem was it said I did not have permission to read the partition info. I got round this by running vmware as "sudo vmware". Now I can see the partitions. I select the FAT32 partition and finish.

When I try to run the virtual machine I get the error :

"Cannot open the disk '/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-2.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file."

How do I solve this?

---

### Post by veloce on 2007-05-17
> **Tridion2000 said:**
> I have Ubuntu Feisty installed and the latest VMWare Server. I have a Windows XP installed as a virtual machine on a 20Gb virtual hard drive. In Ubuntu I also have a 150Gb FAT32 partition which I would like to be able to see in Windows XP. I am trying to add a hard drive in the VMWare settings for this virtual machine.

I select Physical Drive, then "/dev/sda" and then "use individual partitions". The first problem was it said I did not have permission to read the partition info. I got round this by running vmware as "sudo vmware". Now I can see the partitions. I select the FAT32 partition and finish.

When I try to run the virtual machine I get the error :

"Cannot open the disk '/var/lib/vmware-server/Virtual Machines/Windows XP Professional/Windows XP Professional-2.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file."

How do I solve this?

If this drive is mounted by Ubuntu, then what you are trying to do is a Bad Idea(tm).  It's like having a hard disk connected to two computers at the same time - both thinking that they have exclusive access. I think VMWare is protecting you from doing that.

You have two choices: 

[LIST=1]
[*]Make the disk unavailable to Ubuntu.
[*]From Ubuntu, make the disk a samba share and connect to it over the virtual host only network.
[/LIST]

---

### Post by Cellojazz on 2007-05-24
Yes but...

The system user still needs access to the block device ( dev/hdX# or /dev/sdX#)  right?

so...

 How can the root user give block level access to the Ubuntu admin user so that they can see and add the disks in VMWare without sudo-ing or  being root?

I've tried adding the devices to fstab - read only and even as root I don't have "permissions" to chown the mount points to my systemuser. 

What I'm trying to accomplish... 

A VMWare server running from virtual Disks ( Win 2003 Std and SQL 2000) approx 10 GB max
+ A Partition I can use as a native partition to house the SQL Server MDB's  - a 250GB partition

..... While running VMWare server only as the Ubuntu - System User I set up when loading the machine.  I'm going to be using as a multi-user VMWare server, so other users will have their own VMWare server instances also.

I'm really confused on this one, any help is greatly appreciated.

---

### Post by Cellojazz on 2007-05-24
Well I fixed it myself.  I found a link somewhere else that stated, to use partitions you just need to add your user to the DISK group, to have disk admin rights

Code:

sudo useradd <username> disk

and Now it boots up no problem.

If this isn't secure though, I'd like to hear another way around this.

Thanks!

---

### Post by veloce on 2007-05-24
You have made sure that this disk isn't mounted by Ubuntu, yes?  If it is mounted by both the host and the vm it will go horribly wrong!

---

### Post by Trojanmon on 2008-02-27
It's actually sudo adduser<user> disk (not useradd)

---

