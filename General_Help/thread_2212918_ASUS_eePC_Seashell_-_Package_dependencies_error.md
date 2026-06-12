---
title: "ASUS eePC Seashell - Package dependencies error"
date: 2014-03-23
forum: General Help
---

### Post by Satchel88 on 2014-03-23
> E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Screenshot:  [http://s28.postimg.org/5htzly0y5/Screenshot_from_2014_03_23_14_55_39.png](http://s28.postimg.org/5htzly0y5/Screenshot_from_2014_03_23_14_55_39.png)

I'm confused, sorry.  Please help?

---

### Post by CaptainMark on 2014-03-23
You need to use sudo ```
sudo apt-get check
```

---

### Post by Satchel88 on 2014-03-23
Was able to see and un-install the offenders.  (adding -f?)
But anyway, thanks for your help.  I'm way dumb, "sudo" got me where I needed to go.

---

