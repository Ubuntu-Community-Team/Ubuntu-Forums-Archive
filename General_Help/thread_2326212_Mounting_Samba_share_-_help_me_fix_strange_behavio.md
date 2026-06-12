---
title: "Mounting Samba share - help me fix strange behavior"
date: 2016-05-29
forum: General Help
---

### Post by adrian91 on 2016-05-29
Hello,

I'm trying to mount a samba share on a fresh install of Ubuntu 16.04.  I have a NAS running a samba server with 2 shares I would like to access from my Ubuntu box.  Shares are called Media and Documents.  I made two folders in /mnt called Media and Documents respectively to mount the shares into.  When I initially added the share info the the fstab the the folders came back as being owned by root, group root, and permissions of 755.  Not really helpful if only root can write to the share.  I removed the fstab info, unmounted the drives, and changed folder owner to me (adrian) with a group of services (which has a gid of 1001) which I am a part of as well as a few other users (Plex and logitechmediaserver).  This is the way my current fstab is written:

> //atlas/Media       /mnt/Media       cifs        iocharset=utf8,credentials=/home/adrian/.smbcredentials,noperm,dir_mode=0777,gid=1001       0     0

This mounts the drive read only, so I can stream media from my Plex server and Logitech Media server (yay!) but still won't let me or any other user write to the folder. I also tried it without the dir_mode option first, but it exhibits the same behavior.  If I try to make a dummy file with nano it just says no write permissions, but if I do the same thing as root it writes just fine.  It also changes the folder owner to root with group of services.  When I ls -l the folder it spits out 

> drwxrwxrwx  2 root services   0  May 29 1628  Media

which is how I think it should look, but it still won't let me write to the server.  Using the GUI, if I navigate to the share and enter the same username and password that is in the smbcredentials file I get read, write, and execute no problem, so I know the problem is somewhere on the Ubuntu box, not the NAS.  I have to think I'm doing something wrong in my fstab entry, I just don't know what.  Thanks.

---

