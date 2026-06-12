---
title: "vsftpd configuration help"
date: 2005-09-28
forum: General Help
---

### Post by scorpio2002 on 2005-09-28
Hi there!
I'm to configure a ftp server with vsftpd. It works well but I have a problem: when a user logs in, he can go backward into the hyerarchy of the directories up to root. Obviouselly I don't want this to happen: I'd like each user to be restricted to his home dir. How do I do that?

Ciao,
Donato

---

### Post by KingBahamut on 2005-09-28
proftpd is a lot easier to do this with Scorp. 

you might try that instead of vsftpd, but in the case you dont. 

[http://www.netadmintools.com/art355.html](http://www.netadmintools.com/art355.html)
[http://vsftpd.beasts.org/vsftpd_conf.html](http://vsftpd.beasts.org/vsftpd_conf.html)

---

### Post by tomchuk on 2005-09-28
Actually, it couldn't be easier with vsftpd, add or uncomment the following from your /etc/vsftpd.conf:
```

chroot_local_user=YES

```

---

