---
title: "[permissions] Repair permissions"
date: 2007-05-07
forum: General Help
---

### Post by Jules_h on 2007-05-07
Yop;

I've got a problem with the permissions of ubuntu.
After using the chown-command to access some folders, i did have several problems with permissions.
Is there any way to set back the original permissions?

Thanks!

---

### Post by taurus on 2007-05-07
Which directories did you change the permissions?

---

### Post by Jules_h on 2007-05-07
First I did only change the /etc directory, but then I did the biggest mistake of my life :( =
```

chown -hR jules /

```

I did change the user of all the files of my computer to my account. But that did cause several problems, like impossibility to use the sudo command etc...

---

### Post by Jules_h on 2007-05-07
Anyone?

---

### Post by taurus on 2007-05-07
Boot into recovery mode from GRUB menu and do

```
chown -R root /
```

---

