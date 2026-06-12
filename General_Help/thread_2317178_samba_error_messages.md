---
title: "samba error messages"
date: 2016-03-14
forum: General Help
---

### Post by David_Partridge on 2016-03-14
I recently installed Trusty Tahr (14.04.4 LTS Server), and elected to install Samba as part of the install when it was offered .

It seems to work but I am getting error messages:

  ```
At this time the 'samba' binary should only be used for either:
  'server role = active directory domain controller' or to access the ntvfs file server with 'server services = +smb' or the rpc proxy with 'dcerpc endpoint servers = remote'
  You should start smbd/nmbd/winbindd instead for domain member and standalone file server tasks
```

and

```
 ../source3/smbd/server.c:1278(main)
  standard input is not a socket, assuming -D option
```

What if anything have I done wrong (or not) and what needs to be done to correct the situation (I don't anticipate running a DC).

Thanks
Dave

---

