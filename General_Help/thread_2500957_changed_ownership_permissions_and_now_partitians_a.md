---
title: "changed ownership permissions and now partitians are on read only mode"
date: 2024-09-17
forum: General Help
---

### Post by techniciancit on 2024-09-17
Hi everyone, I have ubuntu 22.04 LTS installed on a ssd. I have other installs of mint on the 2nd drive on one partition. Another partition has another version of ubuntu. My main distro is ubuntu and is the one I am logged into now.

The one partition on the 2nd drive  was set on read only and I'm trying to change the permissions and take ownership of that partition so I can copy off some files. In the terminal I typed in the command "sudo chmod 237 /dev/sdb9" and suddenly most of the partitions were marked as read only. I then did "sudo chmod 777 /dev/sdb9" and it hasn't changed. I opened the disks app and I've gone to some of the partitions and I see I've messed up the ownership.

How do I take ownership back and restore it the way it was? I thought 237 changed ownership of the one partitian and 777 changed for all users. I'm still learning Ubuntu so I feel like I properly messed up.

---

### Post by Dennis N on 2024-09-17
> How do I take ownership back and restore it the way it was?  I thought 237 changed ownership of the one partitian and 777 changed for all users.
The **chmod** command does not change ownership, it changes permissions only.

To get a better picture of this situation, find the owner and permissions of the mount point of the filesystem on /dev/sdb9 with terminal command 
**ls -dl path to mountpoint** 
and post the result. Of course, sdb9 has to be mounted at its mount point when you run it. Also change "path to mountpoint" here to the actual path and mount point.

---

