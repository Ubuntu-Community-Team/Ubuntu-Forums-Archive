---
title: "wife cannot log on to Samba share"
date: 2016-03-28
forum: General Help
---

### Post by Dave_Davis on 2016-03-28
I have a Ubuntu 14.04 machine that I just built.  I am using as a file server and development web server.

I have installed LAMP and Samba using tasksel.

Everything works fine except that my wife cannot log onto the machine with her Samba credentials.

I have verified her Samba account and password countless times.  I have verified that she is the owner of her directory.

She has an account on the server and can log in there.

I can log in from all of my windows machines and see/modify all files on all shares.

My account (dmd) is the root account.

All of our Windows machines are W10.

I appreciate all suggestions.

Thanks,

dmd

---

### Post by T.J. on 2016-03-29
> **Dave_Davis said:**
> I have a Ubuntu 14.04 machine that I just built.  I am using as a file server and development web server.

I have installed LAMP and Samba using tasksel.

Everything works fine except that my wife cannot log onto the machine with her Samba credentials.

I have verified her Samba account and password countless times.  I have verified that she is the owner of her directory.

She has an account on the server and can log in there.

I can log in from all of my windows machines and see/modify all files on all shares.

My account (dmd) is the root account.

All of our Windows machines are W10.

I appreciate all suggestions.

Thanks,

dmd


Samba does not support Windows 7/8/10 homegroups.  Microsoft changed the SMB protocol, which means Samba can't use them.  What you can do is edit the /etc/samba/smb.conf file to add a share (e.g.): 


[Shared]
   comment = VM Shared Folder
   path = /home/tj/Shared
   browseable = yes
   read only = no
   valid user = @tj

You may need to restart Samba afterward.  Then use the smbpasswd command to set the password for the user. After the share is set, you will need to use the username and password to get into the share from Windows, but it should work.

---

