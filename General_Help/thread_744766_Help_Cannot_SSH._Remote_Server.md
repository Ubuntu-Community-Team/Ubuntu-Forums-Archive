---
title: "Help: Cannot SSH. Remote Server"
date: 2008-04-03
forum: General Help
---

### Post by sswittch on 2008-04-03
Hi,

I have a co-located server running ubuntu 6.10 and am unable to SSH into it.  This has come about after attempting to install SAMBA and LDAP.  (The reason I attempted to is beyond me as its WAN not LAN)  Anyway, I finished the installation and the last step was to restart LDAP.

Instead I decided to reboot the whole server (again I don't know why).  The machine only starts now with the following processes running.

```
	PIDAscending 	%CPU 	%MEM 	Command 	Nice 	Pri 	RSS 	Stat 	Time 	User
	1 	0.0 	0.0 	init [2] 	0 	23 	664 	S 	00:00:00 	0
	5570 	0.0 	0.0 	/sbin/syslogd 	0 	23 	592 	S 	00:00:00 	0
	7286 	0.0 	0.0 	/usr/sbin/nmbd -D 	0 	23 	1072 	S 	00:00:00 	0
	7287 	0.0 	0.0 	/usr/sbin/nmbd -D 	0 	21 	448 	S 	00:00:00 	0
	7328 	0.0 	0.0 	/usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive 	0 	20 	2156 	S 	00:00:00 	0
	7381 	0.0 	0.0 	/usr/sbin/cron 	0 	23 	2168 	S 	00:00:00 	0
```

The only access I have to this server is through Virtuozzo Control Panel.  I can upload and download files, only I don't know where to start.

The thing that is worse is I have never bothered to backup because I thought linux was unbreakable.  And still believe it is, if the driver knows what they are doing.


Cheers,


Dave.

---

### Post by sswittch on 2008-04-04
Ok I'm wondering if it was a good idea but I decided to look up nmbd and read a post that someone had made.  Unfortunately I am a little dyslexic and read this the wrong way and thought nmbd is spyware, but turns out its part of SAMBA.

So I removed the 2 .sh scripts for SAMBA and SLAPD and had the following result.

```
PIDAscending 	%CPU 	%MEM 	Command 	Nice 	Pri 	RSS 	Stat 	Time 	User
	1 	0.0 	0.0 	init [2] 	0 	23 	664 	S 	00:00:00 	0
	3354 	0.0 	0.0 	/sbin/syslogd 	0 	23 	592 	S 	00:00:00 	0
	5249 	0.0 	0.0 	/usr/sbin/xinetd -pidfile /var/run/xinetd.pid -stayalive 	0 	19 	2156 	S 	00:00:00 	0
	5304 	0.0 	0.0 	/usr/sbin/cron 	0 	23 	2168 	S 	00:00:00 	0
```

I then proceeded to put the SAMBA and SLAPD back where I took them from with no change to the system processes on my next boot.

I'm still faced with the problem of no CLI as I cannont SSH into my server.

---

### Post by sswittch on 2008-04-04
Sorry for bumping this topic, I just have to decide whether or not im going to fly down to the data center and work on it there or not.  

I don't want to spend money if I don't have to.

---

