---
title: "Problems Connecting Ftp Server(Proftpd)"
date: 2007-05-20
forum: General Help
---

### Post by mazki516 on 2007-05-20
Hi!

i've just finished install proftpd and it seems to be working, exept!(lol..) for the connecting problems...
when i'm trying to connect via another computer or from my as well, i get an error that saying "pass reqierd for this user" (this is the error that flashfxp gave me - using onther computer with windows XP), when i'm trying to connect via a simple explorer page it's do nothing....:/
so the q actually is: user in linux, concider as a proftpd user as well? or there is some hidden control panel or config file with the proftpd users...or the problem is something else? 

thanks you all!!
mazki:o

---

### Post by krismatth3 on 2007-05-20
Do you mean "How do you specify a username/password via windows explorer?"  If so, ```
ftp://username:password@ftp-server-ip/
``` will do the trick.

Can you try rephrasing your question? Thank you.

---

### Post by seamuso on 2007-05-20
> **mazki516 said:**
> Hi!

i've just finished install proftpd and it seems to be working, exept!(lol..) for the connecting problems...
when i'm trying to connect via another computer or from my as well, i get an error that saying "pass reqierd for this user" (this is the error that flashfxp gave me - using onther computer with windows XP), when i'm trying to connect via a simple explorer page it's do nothing....:/
so the q actually is: user in linux, concider as a proftpd user as well? or there is some hidden control panel or config file with the proftpd users...or the problem is something else? 

thanks you all!!
mazki:o

The linux user is also a proftpd user .. Are you using the proftpd.conf I posted in your previous thread?

in a terminal ..

sudo /etc/init.d/proftpd stop

once the server is stopped ..

sudo proftpd -n

try logging in from a different machine and see what types of messages you are getting in the console during the login attempts. the -n option doesn't daemonize teh proftpd server so you can ctrl-c to end when you are finished plus you get to see all of the console messages as they happen .. like this -

```

seamuso@bluebuntu:~$ sudo proftpd -n
bluebuntu.bluefrogcs.com - ProFTPD 1.3.0 (stable) (built Thu Mar 8 03:01:15 UTC 2007) standalone mode STARTUP
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - FTP session opened.
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - ANON anonymous: Login successful.
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - Preparing to chroot to directory '/home/ftp'
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - FTP session opened.
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - USER seamuso: Login successful.
bluebuntu.bluefrogcs.com (127.0.0.1[127.0.0.1]) - Preparing to chroot to directory '/home/seamuso/public_html/ftp_root'

```

---

