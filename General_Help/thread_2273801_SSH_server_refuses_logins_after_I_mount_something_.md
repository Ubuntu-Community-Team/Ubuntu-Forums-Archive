---
title: "SSH server refuses logins after I mount something in the folder"
date: 2015-04-15
forum: General Help
---

### Post by Jmolli on 2015-04-15
Hey,

I am having a problem with ssh, to be more precise sftp server. (I am a beginner with ssh/terminal/permissions/linux.)

I am a remote employee, and I did set up a small fileserver so that people in my company could have access to my files. I Installed ssh and configured it so that "user" does have a chroot/jailed/no-shell access what ever it is called (sftp) . That bit was working great and I think I did configure it more or less correct. Then I went and mounted a folder to the "home" folder of the sftp user. 

"mount --bind /source/location/ /user/home/"

After that I cannot anymore connect with ssh to the fileserver... I have a feeling that its because of some permissions. But haven't been able to figure/google it out yet. 
(it works again if I remove the mount)

I don't really understand what I am doing wrong ? or is this the right way of doing it, If I wanna have chrooted user and then share some files from the file system with him ?


-thnx

---

### Post by Jmolli on 2015-04-16
After short night sleep... It suddenly works. I don't have a clue what happened

---

