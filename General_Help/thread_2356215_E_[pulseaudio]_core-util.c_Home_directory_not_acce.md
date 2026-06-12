---
title: "E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied"
date: 2017-03-20
forum: General Help
---

### Post by liminal1 on 2017-03-20
Hi guys, 

I am running the latest version of server, its actually a forked-daapd server. 

shane@AIRLOUNGE:~$ sudo pulseaudio --check
E: [pulseaudio] core-util.c: Home directory not accessible: Permission denied

This also happens when I do arplay -1 (I think thats the command anyway)

Any help would be appreciated?

---

### Post by alexandari on 2017-03-21
Please set the right permissions in your home directory. Review the permissions and if do NOT need to have different users/permissions in your home directory other than your user (shane) you can run 
```
sudo chown -R shane:shane /home/shane
```

---

