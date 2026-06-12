---
title: "Best samba/CIFS configuration to access Windows 10 shared folder"
date: 2016-03-29
forum: General Help
---

### Post by hugo-costelha on 2016-03-29
Hi,

I have a folder shared by Windows 10 which is accessed by different OSes, some of which are Linux. I need to be able to change the files permissions and set/unset the executable bit. I also want the files to have the correct permissions when I use "git".

I have been able to get all of this, but never simultaneously. Either I am able to change the executable bit and a "git checkout" (our simply creating a new file) makes the files executable (even the ones which were not), or the permissions are correct but I am unable to change the executable bit.

I am currently using the following options on my fstab (allows setting the executable bit, but new files are always created with the executable bit):
```
iocharset=utf8,uid=1000,gid=1000,sec=ntlmssp,cifsacl,rw 0 0
```

I have tried using the file_mode option to prevent the executable bit from being set, but it seems that using cifsacl makes smb ignore that option. I even tried adding it to /etc/samba/smb.conf, but to no avail. Unfortunately I was not able to remove the cifsacl option without loosing the ability to set/unset the executable bit of files on the CIFS share.

The shared folder in the server is NTFS.

Thanks for any help.
Hugo Costelha

---

