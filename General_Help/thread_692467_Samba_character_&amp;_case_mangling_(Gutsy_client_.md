---
title: "Samba character &amp; case mangling (Gutsy client and server)"
date: 2008-02-09
forum: General Help
---

### Post by lapsey on 2008-02-09
It seems that smbfs cannot handle non-latin characters or case correctly. It happens with both utf-8 defined (the charset of both systems) and case-sensitive = yes (a variable specific to the share) in smb.conf

Both systems are using Gutsy packages, but I should point out this has been an issue for me for a long time:
samba (3.0.26a-1ubuntu2.3)
smbfs (3.0.26a-1ubuntu2.3)
etc

**So**, both when creating files on client, or reading filenames on client

```
a&#262;ute
&#386;uttes
Çedilla
```

becomes

```
a&#9472;åute
ãéuttes
&#9500;çedilla
```

also, capitalization:
```
:~$ mv music Music

mv: `music' and `Music' are the same file
```

mount command:
```
smbmount //ixion/fnarg /mnt/fnarg -o username=bloop,password=bleep,fmask=755,dmask=755,rw,iocharset=utf8
```


smb.conf:
```
[global]
    ; General server settings
    netbios name = Ixion
    server string =
    workgroup = PANTHEON
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusersYou would think 
    name resolve order = hosts wins bcast
    wins support = yes
    printing = CUPS
    printcap name = CUPS
    syslog = 1
    syslog only = yes

[fnarg]
	path=/home/bloop
	read only=no
	browseable=no
	create mask = 0644
    	directory mask = 0755
	force user = bloop
	force group = bloop
	case sensitive = yes

```

V:(V

What in the heck is up? Either I'm missing a setting or samba has a *lousy* international reputation (charsets support etc)..

---

### Post by jetsam on 2008-02-09
Smbfs, used by the smbmount command, is deprecated and doesn't have very good unicode support.  

Make sure the old mount is unmounted (**sudo umount /mnt/fnarg**), and try:
```
sudo mount -t cifs //ixion/fnarg /mnt/fnarg -o username=bloop,password=bleep,fmask=755,dmask=755,rw,iocharset=utf8
```
...and see if that helps.

---

### Post by lapsey on 2008-02-10
thanks. Cifs works a treat. Much faster, too! :)

Now i just have to work out how to allow mount as user, but that's for another thread

---

