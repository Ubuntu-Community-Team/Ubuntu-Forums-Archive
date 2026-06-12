---
title: "folder owner change automatically in /MNT"
date: 2019-03-23
forum: General Help
---

### Post by alain.roger on 2019-03-23
hello,

for several years now, i mount shared folders from my NAS in /mnt folder.
when i have a /mnt/adata folder in /mnt with owner alain:alain the shared folder is correctly mounted at session start with SMBcredentials data file as suggested in ubuntu documentation.
However for an unknown reason, after few restarts of my computer, the owner od /mnt/adata changed automaticall by root:root and therefore it is not automatically mounted byt /etc/fstab with SMBcredentials data.

1. why does ubuntu change automatically the owner of folder in /mnt?
2. how to solve this issue in order to have my NAS shared folders mounted at the computer starts as previously ?

thx

---

### Post by TheFu on 2019-03-24
The permissions on the unmounted directory don't matter. It is the permissions on the storage device that do matter. Setting the permissions AFTER the mount is done for native Linux file systems "*just works*", as expected.

NTFS permissions are controlled only at mount time, so if you must use NTFS or vfat or FAT32 or xFAT or cifs with storage, the main way to control permissions is with the mount options.  uid=,gid=,username= are the normal ones. To have control, mount using the fstab or autofs, not through a GUI.  There are many examples of these setups in posts inside these forums.  Same for doing samba/cifs mounts.  "fstab cifs credentials=" should find some solutions.  

If that isn't working, then looking at the log files would be my first step.  They would be in /var/log/ somewhere and there is a samba subdir under there which might have client logs.  My autofs logs are in syslog. The mount.cifs manpage has lots of info about permissions and ownership:
```
FILE AND DIRECTORY OWNERSHIP AND PERMISSIONS
       The core CIFS protocol does not provide unix ownership information or
       mode for files and directories. Because of this, files and directories
       will generally appear to be owned by whatever values the uid= or gid=
       options are set, and will have permissions set to the default file_mode
       and dir_mode for the mount. Attempting to change these values via
       chmod/chown will return success **but have no effect**.

```
There is much more in the manpage, along with some caveats and bugs.

```
       In the directory /proc/fs/cifs are various configuration files and
       pseudo files which can display debug information. There are additional
       startup options such as maximum buffer size and number of buffers which
       only may be set when the kernel cifs vfs (cifs.ko module) is loaded.

```

Can you post the mount config line, if the other threads aren't sufficient answers. They may not be.  There are some good experts posting solutions for CIFS mounts in these forums.

I tested that these options are working for me in my autofs setup with the expected owner, group and permissions:
```
-fstype=cifs,rw,iocharset=utf8,uid=thefu,gid=thefu,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials
```

Of course, if your NAS supports NFS, then using that would provide native file permissions and controls over the permissions outside mount settings. And NFS is a little faster than other options.

---

### Post by alain.roger on 2019-03-28
1. after login session is open, if i type in console:
sudo mount -a and password

then the share is mounted correctly.

my issue is that i have to open a console and type there such command, while before a simple command in my fstab file was doing the job.

```
//192.168.1.100/Adata /mnt/adata    cifs vers=1.0,x-systemd.automount,x-systemd.device-timeout=60,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```

Now such command in fstab does not mount automatically the shared folder.

---

### Post by TheFu on 2019-03-28
So you won't be looking at the log files where any issues would be spelled out?

BTW, if that line above is your actual fstab line, there is a space that isn't legal before dir_mode. No spaces are allowed in or between any options.

I did actually test the options in my post above and they worked perfectly here on a 16.04 system connected to a Win7 x64 CIFS server.

It could be a network dependency issue that systemd isn't honoring.  There's a mount option  _netdev which tells mount not to mount it until networking is up.  The logs would say what the issue is, methinks. You can also test using the **smbclient** and manually with **mount -t cifs** ....  Most command line options allow more verbose output which is useful in debugging. The mount command does according to the manpage:
```

       -v, --verbose
              Verbose mode.
```

Please look at the log files around the time you do the mount.

---

