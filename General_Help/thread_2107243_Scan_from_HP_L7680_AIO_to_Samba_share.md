---
title: "Scan from HP L7680 AIO to Samba share"
date: 2013-01-21
forum: General Help
---

### Post by melgish on 2013-01-21
I'm trying to get my "HP Office Jet Pro L7680 All In One" to scan to a network folder shared via Samba and it's just not happening. I had this working fine on Ubuntu Server 10.04.  Now I'm trying to get it going with 12.10.

My server is named "allspice" and lives at 192.168.254.4
My all-in-one is named "hp7680" and lives at 192.168.254.5

This is my smb.conf. This is almost an exact match of what was on my old server. The only difference is the addition of the red line.

```
[global]
        workgroup = CENSORED
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %$
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        load printers = No
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
[COLOR="Red"]        idmap config * : backend = tdb[/COLOR]

[public]
        comment = Family Share
        path = /media/RAID/home
        force user = root
        force group = root
        read only = No
        locking = No

```

When I try to scan, the all-in one immediately reports that it cannot connect.  On the server I can't find any log text to indicate what went wrong but I do see an empty log.192.168.254.5 file created in the /var/log/samba folder. 

I need to know where to look next for diagnostic info.

---

### Post by melgish on 2013-01-27
Update:  The issue seems to be timeout related.  I was able to get it to work a few times over dozens of attempts.

After setting log level = 3, here's what shows up in /var/log/samba/log.192.168.254.5

```

[2013/01/27 19:22:43.319032,  2] param/loadparm.c:8327(do_section)
  Processing section "[public]"
[2013/01/27 19:22:43.319390,  2] param/loadparm.c:8327(do_section)
  Processing section "[work]"
[2013/01/27 19:22:43.319635,  2] param/loadparm.c:8327(do_section)
  Processing section "[backup]"
[2013/01/27 19:22:43.319949,  3] param/loadparm.c:6630(lp_add_ipc)
  adding IPC service
added interface eth0 ip=fe80::201:2eff:fe3a:a930%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.254.4 bcast=192.168.254.255 netmask=255.255.255.0
Allowed connection from 192.168.254.5 (192.168.254.5)
init_oplocks: initializing messages.
Linux kernel oplocks enabled
Server exit (failed to receive smb request)
[2013/01/27 19:22:43.321284,  2] param/loadparm.c:8327(do_section)
  Processing section "[public]"
[2013/01/27 19:22:43.321629,  2] param/loadparm.c:8327(do_section)
  Processing section "[work]"
[2013/01/27 19:22:43.321873,  2] param/loadparm.c:8327(do_section)
  Processing section "[backup]"
[2013/01/27 19:22:43.322182,  3] param/loadparm.c:6630(lp_add_ipc)
  adding IPC service
added interface eth0 ip=fe80::201:2eff:fe3a:a930%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=192.168.254.4 bcast=192.168.254.255 netmask=255.255.255.0
Allowed connection from 192.168.254.5 (192.168.254.5)
init_oplocks: initializing messages.
Linux kernel oplocks enabled
Server exit (failed to receive smb request)

```

So I guess now the question is how to I make Samba wait a few extra seconds for a request.

---

