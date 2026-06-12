---
title: "system complete lockup"
date: 2016-08-21
forum: General Help
---

### Post by cmcanulty on 2016-08-21
I was having trouble with a laptop running xubuntu 16.04. On the admin account after it opens, in about a minute system monitor shows numerous entries for every process and then it reaches 100% cpu and ram and locks up. Can't logout or anything but power off. So today I reinstalled and the same issue. However the non admin account runs perfectly. I need a fix that I can run in a few seconds before everything locks up. Or something I can run from the non admin account from the command line. I thought a new install would fix it but somehow (maybe malware) makes every precess run like 10 or 20 instances. I did keep the /home partition when I reinstalled.

---

### Post by gordintoronto on 2016-08-22
Don't run system monitor, use top from a terminal.

Can you boot from a LiveDVD or USB? Did you recently make any changes to what runs at startup?

Laptop specs?

---

### Post by cmcanulty on 2016-08-22
no but I did a clean install today including /Home and that fixed it but was a lot more work thanks

---

