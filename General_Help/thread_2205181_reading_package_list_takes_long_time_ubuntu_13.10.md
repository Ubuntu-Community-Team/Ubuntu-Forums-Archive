---
title: "reading package list takes long time ubuntu 13.10"
date: 2014-02-12
forum: General Help
---

### Post by nosbor73 on 2014-02-12
just from doing sudo apt-get update 
Reading package list...    
almost 30 minutues

---

### Post by philinux on 2014-02-12
> **nosbor73 said:**
> just from doing sudo apt-get update 
Reading package list...    
almost 30 minutues

Thats far too long. Is your internet connection ok?
```
Fetched 18.9 MB in 24s (759 kB/s)
```

Should be seconds. But check the kB/s that you're getting. 

Try changing the server in System settings> Software and Updates> Look at Download From drop down.

---

### Post by jeanjd63 on 2014-02-12
Hello
You cat try this :
[COLOR=#000000][FONT=Arial][B]sudo  -i
cd /var/lib/dpkg
cp status status.ok
mv status status.sov
mv status.ok  status[/B]
**dpkg --clear-avail**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Then do :
**exit**
and retry  :
**sudo  apt-get  update**[/FONT][/COLOR]

---

### Post by nosbor73 on 2014-02-14
my speed (from talktalk speedtest) was 17.8 MB/s download, so that is ok. 
just ran sudo apt-get update, again it happens
Fetched 961 kB in 7s (135 kB/s)
i wonder if the mirror it reads is slow ?

@jeanjd63
when i do dpkg --clear-avail 
i get
dpkg: error: dpkg status database is locked by another process

---

### Post by jeanjd63 on 2014-02-14
> **nosbor73 said:**
> ........

@jeanjd63
when i do dpkg --clear-avail 
i get
dpkg: error: dpkg status database is locked by another process


Are-you in root to do this command?
If yes have you a process dpkg running in your computer ?

---

### Post by nosbor73 on 2014-02-14
yes i was in root.
i closed down firefox and gvim, then that dpkg clear-avail command worked. not sure what was blocking dpkg, nothing obvious in top.
anyway, i still have the same problem as before.

---

