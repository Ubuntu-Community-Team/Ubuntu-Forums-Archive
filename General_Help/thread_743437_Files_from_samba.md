---
title: "Files from samba"
date: 2008-04-02
forum: General Help
---

### Post by ra300z on 2008-04-02
I've got a Samba server on Ubuntu 7.10 running in my basement (300GB harddrive) accessible by a wireless access point.  I want to upload a photo file that is located on that server to Facebook.  When I go to upload the file using Firefox, it shows all local filesystems in the File dialog, but not network file shares such as Samba.  

Is there a way to do this without mounting Samba as a local filesystem?

---

### Post by discorsage on 2008-04-02
you can use a url for the file :

smb://username@server/folder

---

### Post by ra300z on 2008-04-03
Thanks.

I think it should easier though.  Especially since I don't always know the exact location of my file.

---

### Post by Efros on 2008-04-03
do you mount the drive via fstab?


//172.16.4.154/drive_h /media/h_drive cifs exec,credentials=/etc/cifspw 0 0

The above line mounts a drive (sharename=drive_h) on a remote machine 172.16.4.154) as h_drive. The username and password is stored in the file cifspw with the following format

username=myusernameonthetargetmachine
password=mypasswordonthetargetmachine

---

