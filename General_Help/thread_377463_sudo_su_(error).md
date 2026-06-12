---
title: "sudo su (error)"
date: 2007-03-06
forum: General Help
---

### Post by hudelfa on 2007-03-06
Hi my friends after along time!

I updated  ubuntu dapper drake to edgy eft .and  I got some errors in edgy eft.

1-When I wrote sudo su  in the congole to take root privileges  it appears an error reads `configuration error - unknown item 'FAIL_DELAY' (notify administrator)`. How can I fix this problem.

2-I can not access  my folders in ntfs  partitions any more.I could access before.

---

### Post by Chazall1 on 2007-03-19
I have the same issue after the DST Time Update. In a Terminal, I also get this message when I enter gksu, "Missing command to run"  I still have root access in the regular terminal using sudo su. I do not have any problems using the root terminal. So if you need to have root access, use the root terminal. If anyone has any Ideas!!!!!

Thanks

---

### Post by ardchoille42 on 2007-03-20
The proper command to get a root shell is

```

sudo -i

```

---

### Post by Chazall1 on 2007-03-20
Thank You the sudo -i worked. However when I type gksudo I still get this message when I enter gksudo, "Missing command to run" I have to open a root terminal to be root? 

Any Ideas

Thanks

---

### Post by ardchoille42 on 2007-03-21
> **Chazall1 said:**
> Thank You the sudo -i worked. However when I type gksudo I still get this message when I enter gksudo, "Missing command to run" I have to open a root terminal to be root? 

Any Ideas

Thanks

gksudo is used to run gui apps as root. Try:

```

gksudo gedit

```

---

