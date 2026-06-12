---
title: "Moving /home folder from / (File System Root) to /home partition"
date: 2022-02-14
forum: General Help
---

### Post by ozark_hillbilly on 2022-02-14
I want to move the /home folder location from mount point: Filesytem Root (/) to the mount point: /home.

The sda5 partition which mounts at File System Root is where I want all the Ubuntu files to reside while
my user folder (/home) resides in the sda6 partition mounted at: /home. 

What are the terminal commands to accomplish this or can it be done through Nautilus? 

Attached are screenshots of each partition. 

...thank you...

---

### Post by oldfred on 2022-02-14
To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)
[https://ubuntuforums.org/showthread.php?t=2343317](https://ubuntuforums.org/showthread.php?t=2343317)

---

### Post by ozark_hillbilly on 2022-02-14
Thanks Fred, you young whipper snapper...lol

---

