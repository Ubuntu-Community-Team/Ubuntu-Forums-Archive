---
title: "System information wrong?"
date: 2013-02-26
forum: General Help
---

### Post by Juniorr on 2013-02-26
I downloaded the 12.04.1 a while ago and when I opened the system properties it showed "12.04.1". Last month I downloaded again the 12.04.1 and now it shows only 12.04. What happened? :)

---

### Post by sudodus on 2013-02-26
If your Ubuntu 12.04 system is updated today, 2013-02-26, you should get something like this

```
~$ [COLOR=RoyalBlue]uname -a[/COLOR]
Linux April-2008-precise 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
~$ [COLOR=RoyalBlue]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:  Ubuntu
Description:     Ubuntu 12.04.2 LTS
Release:         12.04
Codename:        precise
~$
```

---

### Post by Juniorr on 2013-02-26
> **sudodus said:**
> If your Ubuntu 12.04 system is updated today, 2013-02-26, you should get something like this

```
~$ [COLOR=RoyalBlue]uname -a[/COLOR]
Linux April-2008-precise 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
~$ [COLOR=RoyalBlue]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
~$
```
Yes. 

(Don't mind my user name, I already have other distros installed so there's also "asd", "qwe", "test", "jr", etc LOL

> zxc@zxc-desktop:~$ uname -a
Linux zxc-desktop 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
> xc@zxc-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
zxc@zxc-desktop:~$ 


---

