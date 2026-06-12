---
title: "CD Drive not detected"
date: 2008-03-22
forum: General Help
---

### Post by xelapond on 2008-03-22
Hello everyone, 

I am having an interesting problem with my CD drive.  When I put a CD into the drive I can access it in Dolphin fine, but when I try and access it within K3B or VirtualBox it is not detected.

I think this may be a group permission error(I had a problem where I got deleted from every group a few days ago), if that helps at all.

Thanks a ton, 

Alex

EDIT: I have an internal ASUS SATA DVD Writer

---

### Post by danwood76 on 2008-03-22
If you run k3b as root does it see the drive?
In terminal:
```

sudo k3b

```

if you do see it and you can burn could you post the output of:
```

id

```

---

### Post by xelapond on 2008-03-22
Yeah, it runs fine in root.

id: 
```
uid=1000(alex) gid=1000(alex) groups=4(adm),5(tty),27(sudo),29(audio),44(video),60(games),108(lpadmin),110(admin),121(vboxusers),1000(alex)
```

Thanks, 

Alex

---

