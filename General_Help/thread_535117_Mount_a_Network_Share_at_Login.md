---
title: "Mount a Network Share at Login"
date: 2007-08-26
forum: General Help
---

### Post by mikaelsnavy on 2007-08-26
OK, this will sound real weird. I am setting up a linux lab at a local school and I am having a problem. I cannot host the user's home folder on a network drive (cause of file permission errors) so I have a copy script running at login and logout that works mostly. It would work a lot better if I could mount. So is there some way to have a script in place of my copy scripts that would mount the network share to the home folder after all the system stuff has loaded? Any help would be a victory for linux!
Thanks,
Mikael

---

### Post by jakev383 on 2007-08-26
Sure.  You can either put the mount command in your copy script, or I'd personally add it to my /etc/fstab and have it mounted at boot time by the OS.
If you give us some more info (what type of share, eg: Windows, NFS, etc.) I'm sure someone will beat me to telling you what the fstab should look like.
[https://help.ubuntu.com/community/MountWindowsSharesPermanently?highlight=%28mount%29](https://help.ubuntu.com/community/MountWindowsSharesPermanently?highlight=%28mount%29)
[https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29](https://help.ubuntu.com/community/SettingUpNFSHowTo?highlight=%28nfs%29)

---

### Post by mikaelsnavy on 2007-08-26
this is where it gets complicated
I got it working perfectly in the /etc/fstab, but I need to have it mounted *after* the user is logged in or as a startup script. I already know where to put the script, I just dont know how to do it (since you usually have to use sudo) is there someway to give it root access for the mount command? I know it has to be like ```
sudo mount -t cifs //netbiosname/sharename /media/sharename -o credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777
``` I cant mount it in the fstab because it fails at logging in (permissions error since the files would be on a 2k3 server). So it brings me back the this, is there some way to use a credentials file like above (I could use username there. but it is more secure this way). 
Thanks,
Mikael
P.S. I hope I am being clear enough, I dont have much linux experience, but more than all the school districts IT department combined!

---

### Post by mikaelsnavy on 2007-08-26
It's all about the sudoers!
I edited the /etc/sudoers file and added 
ALL ALL = NOPASSWD: /bin/mount
ALL ALL = NOPASSWD: /bin/umount
so everyone can mount and unmount. I will test it out on the linux lab I work at on Monday.

---

