---
title: "Can access Samba Share but not Browse?"
date: 2013-03-02
forum: General Help
---

### Post by ejkeebler on 2013-03-02
Ok my issue's a little different and clearly i'm overlooking something stupid.... I can access my samba share via ip or hostname from my W7 and from a terminal from my ubuntu client.  but I cannot for the life of me get it to be seen from under Browse Network/Windows Network (Ubuntu) or under Network (Windows 7)

smbclient -L nas
```


Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.6]

	Sharename       Type      Comment
	---------       ----      -------
	storage         Disk      Comment: /storage
	IPC$            IPC       IPC Service (Samba Share)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.6]

	Server               Comment
	---------            -------
	NAS                  Samba Share
	W7LAPTOP             

	Workgroup            Master
	---------            -------
	WORKGROUP            NAS
```

smb.conf
```
[global]
   bind interfaces only = yes
   browseable = yes
   deadtime = 15
   default case = lower
   disable netbios = no
   dns proxy = no
   domain master = yes
   encrypt passwords = true
   guest ok = yes
   guest only = yes
   hosts allow = 192.168.23. 127.
   hosts deny = all
   interfaces = p4p1
   invalid users = nobody root
   load printers = no
   max connections = 10
   netbios name = nas
   preferred master = yes
   preserve case = no
   printable = no
   read only = no
   security = user
   server string = Samba Share
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=65536 SO_SNDBUF=65536
   strict sync = no
   sync always = no
   syslog = 1
   syslog only = yes
   workgroup = WORKGROUP
   writeable = yes

```

hostname
```
nas
```

---

