---
title: "Mount a SMB share on FSTAB"
date: 2015-02-21
forum: General Help
---

### Post by quirinovix on 2015-02-21
I have a small server (Arch linux) running SAMBA.
On my Ubuntu desktop (14.10, 64 bits) i want to mount a share of that server, with "noauto" option.
But i want any Ubuntu user could mount it. And the share is asking me for authentication, even it being "public".
If a use "guest" option on FSTAB, it do not ask me for credentials. But once a put the "user" option together, i got an error. If i remove the "guest" option, it ask me for password, and i need to hit at least <enter> to get it mounted.

How can i solve this?

My FSTAB:
This alows only root to mount:
```
//<ip server>/share        /mount/point                cifs    guest,rw,noauto 0 0

```
This ask for credentials to mount:```
//<ip server>/share        /mount/point                cifs    user,rw,noauto 0 0

```This get me an error:```
//<ip server>/share        /mount/point                cifs    guest,user,rw,noauto 0 0

```I had also tried to use an external file with credentials, but got error too:```
//<ip server>/share        /mount/point                cifs    user,rw,noauto,credentialfile=/file 0 0

```

Testparm -s:
```

rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[share]"
Loaded services file OK.
Server role: ROLE_STANDALONE


[global]
    server string = Samba Server
    map to guest = Bad User
    log file = /var/log/samba/%m.log
    max log size = 50
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
    load printers = No
    printcap name = /etc/printcap
    dns proxy = No
    idmap config * : backend = tdb
    write cache size = 131072

[share]
    path = /share
    read only = No
    guest only = Yes
    guest ok = Yes
```

---

### Post by TheFu on 2015-02-21
If you like, you can specify the specific userid/group that does the mount and just ensure that everyone who does the mount is in the group with write permissions. [https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide) says: > The user you specified with guest account in the [global] section must have write permissions on /path/to/share/point in order to write files to the share.
gui/uid are the options - be certain the file and directory create settings allow group r/w.

Honestly, for Linux-to-Linux sharing, perhaps NFS is easier?  It will allow groups and normal file permissions to be shared across both systems.  I use NFS as though it is local storage ... plus it is faster than samba. the only trick with NFS is that userids and group ids for the shared storage need to be identical between the systems ... or come from a central store - like LDAP or NIS+.

Consider using autofs for remote and USB mounting. That way the mount is delayed until someone actually tries to use files in the directory where it would be mounted. Don't think that matters.

BTW, do you need to specify "browseable = yes" in the [share] stanza?

Another option is to see if a file browser like nautilus, thunar, pcmanfm can mount the storage with gvfs instead of using /etc/fstab.  Might be a workaround (even if I hate, hate, hate, gvfs personally).

Don't forget that you can turn up logging for the server side and see what is failing in those log files. Usually those errors jump out and are very clear with the root issue. At least that has been my experience.

---

### Post by bab1 on 2015-02-21
> **quirinovix said:**
> I have a small server (Arch linux) running SAMBA.
On my Ubuntu desktop (14.10, 64 bits) i want to mount a share of that server, with "noauto" option.
But i want any Ubuntu user could mount it. And the share is asking me for authentication, even it being "public".
If a use "guest" option on FSTAB, it do not ask me for credentials. But once a put the "user" option together, i got an error. If i remove the "guest" option, it ask me for password, and i need to hit at least <enter> to get it mounted.

How can i solve this?

My FSTAB:
This alows only root to mount:
```
//<ip server>/share        /mount/point                cifs    guest,rw,noauto 0 0

```
This ask for credentials to mount:```
//<ip server>/share        /mount/point                cifs    user,rw,noauto 0 0

```This get me an error:```
//<ip server>/share        /mount/point                cifs    guest,user,rw,noauto 0 0

```I had also tried to use an external file with credentials, but got error too:```
//<ip server>/share        /mount/point                cifs    user,rw,noauto,credentialfile=/file 0 0

```


Mounting the SMB file system in this context shouldn't have anything to do with the Samba configuration.  You should use the parameter ***users*** in fstatb if you want *_all users _*to be able to mount the share.  From the mount man page```
      [COLOR="#FF0000"]users  Allow every user to mount and unmount the filesystem[/COLOR].  This option implies the
              options noexec, nosuid, and nodev (unless overridden by subsequent options, as
              in the option line users,exec,dev,suid).

```

---

