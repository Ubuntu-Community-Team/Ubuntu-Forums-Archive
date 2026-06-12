---
title: "Accessing Samba Shares Created by GUI"
date: 2008-06-03
forum: General Help
---

### Post by jjrev on 2008-06-03
I'm running 64-bit Ubuntu 8.04.  

I've created a samba share from the GUI and only checked "Share this Folder" and "Allow other people to write in this folder".  I'm unable to mount the share from my WinXP machine.  When I try to "Map Network Drive" from WinXP, it keeps asking me for my password.  No matter what I enter for the password, the drive will not mount.  

I don't have anything related to my share in /etc/samba/smb.conf (Should I?)

Please help :confused:

---

### Post by sisco311 on 2008-06-03
Did you setup a samba password?

In the *Shared Folders* select the *Users* tab, click the *Unlock* button,
enter your admin password, and select your user name(or real name)
and enter your samba password.

Or you can do this from the terminal:
```
sudo smbpasswd -a $USERNAME
```To create a new samba user(for a windows user):
```
sudo useradd **username**
sudo smbpasswd -a **username**
```To restart the samba server:
```
sudo /etc/init.d/samba restart
```

---

### Post by jjrev on 2008-06-03
I don't know of this "Shared Folders" you mentioned.  

I did the "sudo" commands, but now when I try to mount the network drive, I get a Windows Error telling me: "The mapped network drive could not be created because the following error has occurred: \nAn extended error has occurred." (Isn't windows wonderful ;))

---

