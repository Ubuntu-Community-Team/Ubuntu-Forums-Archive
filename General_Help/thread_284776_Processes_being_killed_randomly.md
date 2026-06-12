---
title: "Processes being killed randomly"
date: 2006-10-26
forum: General Help
---

### Post by deags on 2006-10-26
CPU Speed  	847.56 Mhz
Physical Memory  	123.43 MB, 2.13 MB FREE
Disk Swap  	486.30 MB, 416.19 MB FREE

There is heaps of swap!

Why would the processes be getting killed? They are not very intensive. Any help?

This is annoying me alot.

---

### Post by devnull73 on 2006-10-26
bad ram?

---

### Post by deags on 2006-10-26
i strongly doubt it

---

### Post by jordilin on 2006-10-26
type 
```
ps ax
```
and show us what kind of processes are being killed.

---

### Post by deags on 2006-10-26
> 8937 ?        S      0:00 /usr/bin/perl -I /var/www/Qmgr /var/www/Qmgr/Qmgrd.pl /media/external/ 10 10 localhost 2606
 9215 ?        S      1:54 /usr/bin/python -OO /var/www/TF_BitTornado/btphptornado.py
 9236 ?        S      0:39 /usr/bin/python -OO /var/www/TF_BitTornado/btphptornado.py
 9252 ?        S      0:43 /usr/bin/python -OO /var/www/TF_BitTornado/btphptornado.py
 9268 ?        S      1:50 /usr/bin/python -OO /var/www/TF_BitTornado/btphptornado.py

they are the ones i notice

---

### Post by deags on 2006-10-27
anyone know why it does this? it is really making me get annoyed :(. I don't really have the time to go format and installed a different os.

---

### Post by deags on 2006-10-29
i think i may have sold it.... lighttpd was getting restarted everyday for some log thing....

---

