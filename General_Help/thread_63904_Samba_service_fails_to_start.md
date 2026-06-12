---
title: "Samba service fails to start"
date: 2005-09-09
forum: General Help
---

### Post by Teo on 2005-09-09
Hi,
It's too big for me :/

Ubuntu machine can't start samba service at a bootup time - in screenlog it displays: samba [fails].

This is what I get when start samba by hand:
```
tomek@teo:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...          [ ok ]
 * Starting Samba daemons...          [fail]
```

/var/logs/samba/log.smbd shows only this:
```
[2005/09/09 16:34:34, 1] auth/auth_util.c:make_server_info_sam(840)
  User guest in passdb, but getpwnam() fails!
```

Here's my smb.conf file: [link](http://www.amit.neostrada.pl/smb.conf)

---

### Post by Teo on 2005-09-09
[QUOTE=Teo]Hi,
It's too big for me :/

Ubuntu machine can't start samba service at a bootup time - in screenlog it displays: samba [fails].

This is what I get when start samba by hand:
```
tomek@teo:~$ sudo /etc/init.d/samba restart
 * Stopping Samba daemons...          [ ok ]
 * Starting Samba daemons...          [fail]
```

/var/logs/samba/log.smbd shows only this:
```
[2005/09/09 16:34:34, 1] auth/auth_util.c:make_server_info_sam(840)
  User guest in passdb, but getpwnam() fails!
```

Here's my smb.conf file: [link](http://www.amit.neostrada.pl/smb.conf)[/QUOTE]
 OK case solved:
sudo smbpasswd -x guset

There's other thing:
I have two shares: [Home] and [My Music]. Right now I can acces them by loggin into my local account (Authentication=Yes) - pls see my smb.conf (link i first msg). But I want to acces [My Music] (and olny [My Music] without logging (I want to share it for all hosts in my LAN without authentication).
How I can do that?

---

### Post by GTvulse on 2005-09-09
If you are running the Samba server as a standalone server (the default), each Windows user registered in the Samba server must be a user registered in the system. That is, there must be an OS user called guest (or whatever, Samba can match system user names to Windows user names) even if it is a locked out account with no home directory.

BTW, you may want to reconfigure Samba to use passwords **different** to the system ones. Installing SWAT and using it for server administration will be a great help (you just point your web browser to [http://localhost:901/)](http://localhost:901/)).

---

### Post by Teo on 2005-09-09
[QUOTE=dradul]If you are running the Samba server as a standalone server (the default), each Windows user registered in the Samba server must be a user registered in the system. That is, there must be an OS user called guest (or whatever, Samba can match system user names to Windows user names) even if it is a locked out account with no home directory.[/QUOTE]
How to create OS user 'guest' without home directory in Ubuntu?

---

