---
title: "Automounting Samba Share in /etc/fstab"
date: 2013-12-03
forum: General Help
---

### Post by Noah0504 on 2013-12-03
I've done this is the past, but on a new server install, I for the life of me, can not figure out why it's not working this time around.

The Samba share I have DOES allow guest access, and that's how I access it, in fact.

This is the entry I have in /etc/fstab:
```
//SERVER/SHARE /media/SHARE cifs guest,_netdev 0 0
```

I do have cifs-utils installed, but the error I'm receiving is "mount error(13): Permission denied".  I've double checked everything a 100 times, but just can't figure out what's going on.

Thanks in advance!

---

### Post by bab1 on 2013-12-03
> **Noah0504 said:**
> I've done this is the past, but on a new server install, I for the life of me, can not figure out why it's not working this time around.

The Samba share I have DOES allow guest access, and that's how I access it, in fact.

This is the entry I have in /etc/fstab:
```
//SERVER/SHARE /media/SHARE cifs guest,_netdev 0 0
```
I do have cifs-utils installed, but the error I'm receiving is "mount error(13): Permission denied".  I've double checked everything a 100 times, but just can't figure out what's going on.

Thanks in advance!

Post the output of these commands```

testparm  --section-name <share_name>

ls -l /mnt

ls -l /mnt/SHARE

```...where <share_name> is the name of the share you are trying to mount.


These will show the access and authorization of the share and its underlying file system.  The term guest in the above fstab file only suppresses the request for a login and password.  It does not negate the share or file system security.

---

### Post by Noah0504 on 2013-12-28
I took a break from this problem because of a busy schedule, but finally revisited it.  This time I was trying to get it to work on a Raspberry Pi running Rasbian.  Anyway, I had the same problem as before, so I figure it must be something with my NAS.  I had this working with the same hardware earlier in the year, but something changed... maybe the version of CIFS on the computers, I'm not sure.

Anyway, I was able to finally get it to work by adding the following: ```
sec=ntlmv2
```

---

