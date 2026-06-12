---
title: "cannot access files"
date: 2017-05-05
forum: General Help
---

### Post by relic2 on 2017-05-05
I am somewhat new to Linux. My background is in network engineering and I work with Linux daily. I have come across an issue with my personal Ubuntu 16.04 box that I have spent 2 weeks trying to solve ](*,). This issue with with the package tftp-hpa. The install went seamless and worked for over a month, then it just quit allowing files to be written or read. I have spent countless hours in forums to no avail. I am in need of a willing expert to help me figure out what in world is happening. It seems all of the directories and files are no longer accessible by any user or group other than root. I cant access the contents logged into cli using sudo <admin username>, however when browsing using the same user via sftp, I am denied access. I have tried changing the owner and permissions and nothing seems to work. 

WinSCP error listing directory message:
Permission denied.
Error code: 3
Error message from server: Permission denied

Error seen from cli logged is as admin user
<omitted>@ubuntu-server:~$ cd /srv/tftpboot/
-bash: cd: /srv/tftpboot/: Permission denied

I have verified the owner to be tftp as instructed in the installation guide and have changed the group from nobody to a created group called tftp. The user ID logged in trying to access the files is a part of the tftp group along with root. 


This directory is far from empty, is has quite a lot of data for several devices I personally manage. My backup scripts are all failing and network gear is no longer able to get or put any files. 

Please help

---

### Post by relic2 on 2017-05-05
I forgot a environmental issue that was experienced. I was working remotely and all files and folders were locked down for some reason. I don't remember what the command that was used to unlock the files and folders. I do know the issue started shortly, if not immediately after that event.

---

