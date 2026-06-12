---
title: "unable to create ext4 partition on hard drive"
date: 2023-08-04
forum: General Help
---

### Post by rebeltaz on 2023-08-04
For data backup storage, I buy used 500gb laptop hard drives off ebay and access them via a USB docking station. I've been formatting them in fat32, but tonight I tried using ext4. I used gparted first, like I always do when I format to fat32. It said that everything went fine, so I ejected the drive and reconnected it. It showed up and I could see the lost+found directory, but I was not able to write anything to it. When I looked at Properties (in nemo) it showed that it was owned by root and that I did not have access. So I tried formatting and partitioning in fdisk and mkfs.ext4, still using ext4. Same results. Finally, I went back to gparted and formatted and partitioned the drive to fat32. I am writing data to it now just fine. 

Does anyone have any idea what I am doing wrong? I know I have done this before with no problems.

---

### Post by ajgreeny on 2023-08-04
You are not doing anything wrong; by default ext4 partitions are owned by root after creation and their ownership must be changed to you as user using a simple. chown command.

Firstly make sure that the ext4 partition has a label eg "data" as it makes life simpler as the mountpoint of that data partition will be **/media/username/data**

Now run command ```
sudo chown username:username /media/username/data
``` Use your actual username of course.
You will now be able to read and write to that partition as user.

---

### Post by rebeltaz on 2023-08-04
Huh... I don't remember ever having to chown the partition in the past when I used ext4. Is this new in recent versions of Ubuntu or has it always been that way? It's probably been a while since I've done it and I do have the memory of a guppy, so... ¯\_(&#12484;)_/¯
 
I appreciate it, though. And yeah... I do need to change that label. When I did it, that freaking thing was a mile long! lol Thanks again.

---

### Post by yancek on 2023-08-05
Drive partitions on external drives have always been owned by root as a default AFAIK so you would need to chown to write to it.  Also, fat32 and ntfs filesystems don't use or understand Linux permissions (rwx).  Generally speaking, a normal user has rw permissions on the /home/username directory and not much else as a default.

---

