---
title: "Problems with Samba on Ubuntu on IBM Power8 (little endian)"
date: 2015-02-26
forum: General Help
---

### Post by Franco_Lombardo on 2015-02-26
Hi all, 
I'm running Samba 4.1.6 with Ubuntu 14.04.1 LTS Little Endian on a Power8 box. 
I wrote this smb.conf file:  
```

[global]
  netbios name = linux01
  log level = 3
  workgroup = mygroup
  server string = %h server (Samba, Ubuntu)
  wins support = no
  dns proxy = no
  log file = /var/log/samba/log.%m
  max log size = 1000
  syslog = 0
  panic action = /usr/share/samba/panic-action %d
  server role = standalone server
  passdb backend = tdbsam
  obey pam restrictions = yes
  unix password sync = yes
  passwd program = /usr/bin/passwd %u
  passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
  pam password change = yes
  map to guest = bad user
  usershare allow guests = yes


[smbshare]
  path = /home/myuser/smbshare
  available = yes
  valid users = myuser
  read only = no
  browseable = yes
  public = yes
  writable = yes

```


When I try to connect to the samba share from Windows 7 I get this error:


"System error 64 - the specified network name is no longer available". 
In the /var/log/samba/log.my.client.ip.address I read:
```




[2015/02/26 11:14:44.715805,  3] ../source3/lib/access.c:338(allow_access)
  Allowed connection from x.x.x.x (x.x.x.x)
[2015/02/26 11:14:44.716146,  3] ../source3/smbd/oplock.c:870(init_oplocks)
  init_oplocks: initializing messages.
[2015/02/26 11:14:44.716306,  3] ../source3/smbd/process.c:1795(process_smb)
  Transaction 0 of length 4 (0 toread)
[2015/02/26 11:14:44.716363,  2] ../source3/smbd/process.c:1823(process_smb)
  Non-SMB packet of length 0. Terminating server
[2015/02/26 11:14:44.716506,  3] ../source3/smbd/server_exit.c:212(exit_server_common)
  Server exit (Non-SMB packet) 



```


In log.nmbd I see:

```

[2015/02/26 11:27:17,  0] ../source3/nmbd/nmbd_packets.c:1397(validate_nmb_packet)  validate_nmb_packet: Bad QUERY Packet. validate_nmb_packet: Ignoring request packet with opcode 0.
[2015/02/26 11:27:17,  0] ../source3/nmbd/nmbd_packets.c:1397(validate_nmb_packet)
  validate_nmb_packet: Bad QUERY Packet. validate_nmb_packet: Ignoring request packet with opcode 0.
[2015/02/26 11:27:17,  0] ../source3/nmbd/nmbd_packets.c:1397(validate_nmb_packet)
  validate_nmb_packet: Bad QUERY Packet. validate_nmb_packet: Ignoring request packet with opcode 0.
[2015/02/26 11:27:17,  0] ../source3/nmbd/nmbd_packets.c:1397(validate_nmb_packet)
  validate_nmb_packet: Bad QUERY Packet. validate_nmb_packet: Ignoring request packet with opcode 0.
[2015/02/26 11:27:17,  0] ../source3/nmbd/nmbd_packets.c:1397(validate_nmb_packet)
  validate_nmb_packet: Bad QUERY Packet. validate_nmb_packet: Ignoring request packet with opcode 0.

```

Note that I can't connect to this share neither from Windows nor from Linux, and that the same configuration runs fine on Ubuntu Server on Windows. 
  
Thanks in advance. 
  
Bye 
  
Franco

---

