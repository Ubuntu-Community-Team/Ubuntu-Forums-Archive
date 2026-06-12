---
title: "Symlinks, /etc/skel question"
date: 2007-12-25
forum: General Help
---

### Post by Nexusx6 on 2007-12-25
Hey everyone. I have two relativity simple questions about symlinks and creating new users.

I have an FTP server I'm getting set up; what I'm trying to do is give each user Read Write eXecute permissions for their home directory, while having a folder in each of their home directories that points to a "shared" directory with Read permisions, but no W or X.  

Basically, what I want is to let people upload and download personal files from their directory, while letting them download things I've placed in shared directory but no to edit/upload to that directory. I know how to do this with owner and group permisions, so my question is as follows:

1) Where should I put this shared directory in the linux file system? Say I wanted to call this folder "Public", is /usr/shared/public an appropriate place? Or should I place it under the user 'ftp' that vsftpd made on install (/home/ftp/public)

2) I like this Symlink to be part of every user, so is there way I can use /etc/skel so that every user I create automaticly gets this symlink to the directory?

3) How should I link to this directory? is
```
ln -s /usr/shared/public /home/[usrname]/public/
```
the correct code?

Thanks for the help :KS

---

