---
title: "gproftpd and proftpd"
date: 2008-03-03
forum: General Help
---

### Post by Woody1987 on 2008-03-03
Hi, using gproftpd i am able to activate and deactivate ftp whenever i please when i am at the computer locally but i would like to be able to do it remotely through ssh. The reason for this is that i left it on over a weekend and checked the logs, and i found several hundred attempts and trying to gain access. I therefore dont want to leave it on all the time. The solution i want is to be able to keep it deactivated and then connect to the ftp server through SSH and activate it and the deactivate it when i am finished. The problem i have is that SSH only gives a command line interface and i do not know how to activate and deactivate proftpd this way. Any help would be appreciated.

---

### Post by Woody1987 on 2008-03-03
bump

---

### Post by mcphargus on 2008-03-03
[here's a tutorial on installing and configuring proftpd from command line]("http://archiv.debianhowto.de/en/proftpd/c_proftpd.html#proftpd_howto")

the last-ish step asks you to restart your inetd, when you do this, it might kick you out of ssh, wait a minute or so and then log back in if it does.

---

### Post by Oldsoldier2003 on 2008-03-03
> **Woody1987 said:**
> Hi, using gproftpd i am able to activate and deactivate ftp whenever i please when i am at the computer locally but i would like to be able to do it remotely through ssh. The reason for this is that i left it on over a weekend and checked the logs, and i found several hundred attempts and trying to gain access. I therefore dont want to leave it on all the time. The solution i want is to be able to keep it deactivated and then connect to the ftp server through SSH and activate it and the deactivate it when i am finished. The problem i have is that SSH only gives a command line interface and i do not know how to activate and deactivate proftpd this way. Any help would be appreciated.
better yet remove ftp completely, use ssh and allow sftp. its more secure, and even windows users can use it with gui clients like filezilla

---

### Post by Woody1987 on 2008-03-03
ok, so i have now decided to go with sftp as mentioned previously, how do i now setup a sftp server?

---

### Post by Woody1987 on 2008-03-03
nevermind, its all sorted now

---

