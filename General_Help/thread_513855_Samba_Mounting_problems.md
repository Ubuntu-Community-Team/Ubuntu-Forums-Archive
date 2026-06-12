---
title: "Samba Mounting problems"
date: 2007-07-31
forum: General Help
---

### Post by charper_99 on 2007-07-31
I have two linux machines (and a bunch of windows ones - but they're not important) on a network.   For a long time, I had a samba server running in Fedora 7, but I had to make a configuration change to allow windows users to have write permissions to a directory without needing a username/password.  This, however, broke my automount in the Ubuntu client.

The samba server's samba.conf file:
```
[global]
	workgroup = workgroup
	netbios name = charper-fs

[Raid]
	comment = 1TB Raid Array
	path = /mnt/raid
	read only = no
	guest ok = yes
	writable = yes

```


I can connect to this server just fine using Gnome's interface, but I can't seem to mount it...

This USED to work
in fstab:
```
//charper-fs/Raid /mnt/charper-fs/ smbfs username=defaults,password=defaults 0 0
```

but it now returns: "8612: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed"

I've also tried install winbind and switching to cifs using this code:
```
//charper-fs/Raid/ /mnt/charper-fs cifs guest,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

and this returns: "mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)"


I've tried countless little variations of the two lines listed here, but I'm obviously missing something.  Any help would be appreciated.

---

### Post by charper_99 on 2007-07-31
SOLVED - thanks for the help guys... well, in the other forum anyway... I had to change both computers configurations

fstab:
```
charper-fs:/raid /mnt/charper-fs/ cifs defaults 0 0
```


samba server:
```
[global]
	workgroup = workgroup
	server string = 1 TB Raid array
	security = share
	guest ok = yes
	guest account = samba

[raid]
	comment = 1 TB Raid Array
	path = /mnt/raid
	writeable = yes
	guest ok = yes
```

---

