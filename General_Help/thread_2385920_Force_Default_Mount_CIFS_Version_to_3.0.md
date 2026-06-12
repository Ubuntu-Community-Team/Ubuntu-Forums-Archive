---
title: "Force Default Mount CIFS Version to 3.0"
date: 2018-02-26
forum: General Help
---

### Post by Steven_Johnson on 2018-02-26
I'm running Ubuntu Server 16.04.3 LTS 64-Bit with cifs-utils installed, as a VM, on a VMWare ESXi 6.5 hyper-visor.
  I have a regular network share setup on Windows Server 2016.
  The objective is to utilize Veeam Linux Agent to Backup this Linux VM to a Windows Share via CIFS.


  **The Problem:**

  When I am configuring Veeam to use CIFS, (viewing the logs) veeam is executing this command to connect to the network share:
```

mount -t cifs -o username=MyUsername,password=*,rw,soft //MyServerIP/MyShare /tmp/veeam/MyServerIPMyShare

```

It gives me the error: mount error(112): Host is down.  When I run the command manually, it does the same thing.
  However when I run the command like this:
  ```

mount -t cifs -o vers=3.0,username=MyUsername,password=*,rw,soft //MyServerIP/MyShare /tmp/veeam/MyServerIPMyShare

```

 It mounts without issue same if I use 2.0 as well.
  The problem is, there is no way to force version 3.0 in Veeam. So, I need to be able to force this in Linux some how.
  I've seen others have ran into this issue as well, but no solution was presented.
  I've attempted the following (based on what I found):
  Added the following lines to   /etc/samba/smb.conf
  ```
server min protocol = SMB2
server max protocol = SMB3
client min protocol = SMB2
client max protocol = SMB3
min protocol = SMB2
max protocol = SMB3
client ipc min protocol = SMB2

```
I mixed and matched variations with reboots, to no avail.

---

### Post by adamveatch on 2018-03-05
Chiming in with the same request. Got a Ubuntu 16.04 LTS box that needs Veeam installed and configured to backup to a Windows box.

---

