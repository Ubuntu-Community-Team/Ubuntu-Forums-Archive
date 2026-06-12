---
title: "samba error: &quot;protocol negotiation failed&quot;"
date: 2006-12-05
forum: General Help
---

### Post by orzechowskid on 2006-12-05
I have two machines on my LAN - a WinXP SP1 machine, and my Ubuntu Edgy machine.  I'm trying to view the WinXP shares from Ubuntu, but no matter what I try I'm given the error "protocol negotiation failed".  I believe smbclient works properly since I can connect to localhost and see my own shares...

```
dan@local:~$ smbclient -d3 -U dan -L 127.0.0.1
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.1.10 bcast=192.168.1.255 nmask=255.255.255.0
added interface ip=192.168.2.1 bcast=192.168.2.255 nmask=255.255.255.0
Client started (version 3.0.22).
Connecting to 127.0.0.1 at port 445
Password:
```

...but I can't seem to connect to the Windows machine...

```
dan@deo:~$ smbclient -d3 -U dan -L 192.168.1.11
lp_load: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface ip=192.168.1.10 bcast=192.168.1.255 nmask=255.255.255.0
added interface ip=192.168.2.1 bcast=192.168.2.255 nmask=255.255.255.0
Client started (version 3.0.22).
Connecting to 192.168.1.11 at port 445
protocol negotiation failed

```

...and I can't figure out why.

Both machines are on the same subnet (192.168.1.x) and in the same workgroup.  I'm not at home at the moment so I can't get any logs from the WinXP machine, but I should be able post 'em later if necessary.

Anyone have any ideas?  Thanks in advance!

---

### Post by Iowan on 2006-12-05
Windows firewall?
(Is it running, does it allow sharing?)

---

### Post by orzechowskid on 2006-12-05
hi, thanks for your quick response.  I'll check again when I get home, but I don't think the firewall is the problem.

when I try to mount the share via cifs, I get a permission denied error:

```
root@local:/home/dan# mount -t cifs //192.168.1.11/C$ /mnt/xp
Password:
mount error 13 = Permission denied

```

when I try to mount a non-existent share, I get a share not found error:

```
root@blocal:/home/dan# mount -t cifs //192.168.1.11/dingus /mnt/xp
Password:
retrying with upper case share name
mount error 6 = No such device or address

```

To me at least, that means my machine is aware of the remote machine and can find out which shares are real and which ones aren't; that seems to imply a configuration problem, not a firewall problem.

(And I would try to just mount the shared directory I'm interested in, but I have a separate permissions problem to work out first and danged if I can remember the name of the publicly-accessible one right now...)

---

