---
title: "Automatic start up"
date: 2004-11-08
forum: General Help
---

### Post by chet on 2004-11-08
Hi All, how would I get a daemon to start automatically when I start my laptop, I need to get /usr/sbin/nessusd -d to run on start up but with root privileges

Cheers

Chet

---

### Post by Slapdash on 2004-11-08
I'm a noob so take this with a LOT of salt ;)

I guess finding the startup conf. file and editing that?  I'm just participating so wait for a more experienced user. ;)

---

### Post by fng on 2004-11-08
i think:
```
$> sudo update-rc.d /usr/sbin/nessusd defaults
``` 

dunno about the -d option to be honnest

try 
```
$> sudo update-rc.d '/usr/sbin/nessusd -d' defaults
``` 
or
```
$> sudo update-rc.d "/usr/sbin/nessusd -d" defaults
```

---

