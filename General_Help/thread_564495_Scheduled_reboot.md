---
title: "Scheduled reboot"
date: 2007-10-01
forum: General Help
---

### Post by AndyD on 2007-10-01
Hi,

I would like to get Ubuntu 6.10 server to reboot at 02:00 each day.

I have:
1. log in as root
2. crontab -e
3. added    00 02 * * * reboot
And nothing happened at 02:00
4. removed the reboot line
5. added 00 02 * * * shutdown -r now
again nothing happened

I can see the entries in /var/log/syslog 

Oct  1 02:00:01 prubuntu /USR/SBIN/CRON[21658]: (root) CMD (shutdown -r now)

Any suggestions welcomed :-)

---

### Post by scruff on 2007-10-01
Try:

```

0 2 * * * /sbin/reboot

```

Not sure if this is your problem, but if nothing is happening using the full path explicitly might get you there. I've never used '00' or '02' either. Single digits work fine unless 2 are required (i.e. 23).

---

### Post by Vlet on 2007-10-01
I'm just curious why you would want to do this.

---

### Post by scruff on 2007-10-01
Heh - I thought of asking that question. I look at my Gentoo box that has 245 days of uptime and going strong now and always. Certainly there's a better reason than "because Windows generally requires it"? :P

---

### Post by AndyD on 2007-10-03
Hi guys,  I will try the full path.

The reason.....the box is running as a NATting box,  redirecting incoming traffic to relevant servers and for some reason it locks up once a month.  Presumably some table is filling up but I don't where to start,  so a scheduled reboot at 2am on a sunday will get me around it for now.

---

### Post by AndyD on 2007-10-03
Woohoo...gj scruff.

Thnx all.

Unless someone can tell me where to start with working out why it might lock up?  ;)

---

### Post by scruff on 2007-10-03
I see. You could try poking around in /var/log/ (particularly debug, messages[.*], acpid, & syslog). Might be some useful info there. Note that those logs get rotated, so looking at the tar.gz'd ones would get you back so many days.

---

### Post by AndyD on 2007-10-03
Info much appreciated....I will do some delving next time I get the chance.

---

