---
title: "Samba started giving a &quot;signal 11&quot; error"
date: 2016-04-20
forum: General Help
---

### Post by ^_Pepe_^ on 2016-04-20
Hi all. 

I have a 14.04 server very very stable, with samba and other multimedia family utilities.

Happy so far, but since few days, the behaviour accesing the server is that randomly the server refuses the files. The /var/log/samba complains about a 

```
[2016/04/20 23:01:15.879743,  0] ../lib/util/fault.c:79(fault_report)
  INTERNAL ERROR: Signal 11 in pid 17644 (4.3.8-Ubuntu)
  Please read the Trouble-Shooting section of the Samba HOWTO
[2016/04/20 23:01:15.879743,  0] ../lib/util/fault.c:81(fault_report)
```

but looking for these in google, gives me very old posts.

samba version is 4.3.8

Also complains about 

```
  process_usershare_file: stat of /var/lib/samba/usershares/2teras failed. Permission denied
```

but I've never have modified permissions. Everyone at home can access everywhere.

I'd appreciate any help
^_Pepe_^

I'm attaching a link to the one window machine's  log

[https://dl.dropboxusercontent.com/u/11614522/log.barney](https://dl.dropboxusercontent.com/u/11614522/log.barney)

Attaching also the guest granted acccess

[https://dl.dropboxusercontent.com/u/11614522/Captura%20de%20pantalla%20de%202016-04-20%2023%3A34%3A03.png](https://dl.dropboxusercontent.com/u/11614522/Captura%20de%20pantalla%20de%202016-04-20%2023%3A34%3A03.png)

Thanks

-----------------------------
Edit: I've started a bug in Launchpad [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573181](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/1573181)

---

