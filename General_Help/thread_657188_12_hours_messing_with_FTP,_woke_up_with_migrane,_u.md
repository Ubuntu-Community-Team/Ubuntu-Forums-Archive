---
title: "12 hours messing with FTP, woke up with migrane, ugh"
date: 2008-01-03
forum: General Help
---

### Post by krelkor on 2008-01-03
My head hurts, i cant seem to get FTP working on my ubuntu box

Ive gone through countless tutorials on both proftpd as well as vsftpd. 

When vsftpd is up and running, i immediatly cannot connect because of a 500 error, and with proftpd running i cant even connect to the server


Is there one key thing im missing? Is there an output i can post from either of these programs that will help you guys diagnose whats going on?


It stinks, all i want an ftp server for is to backup my BWLOG from my dd-wrt router :(

---

### Post by phibit on 2008-01-03
The main issue I had with setting up an FTP server was router pass-through. What I ended up doing was just forwarding all traffic from ports 22 and 21 to my NAT IP. Apart from the that, I just followed a proftpd tutorial and It was successful.

---

### Post by krelkor on 2008-01-03
thanks for the reply, is this something i have to do even if im doing this internally on my lan?

---

### Post by phibit on 2008-01-03
Oh you just want the FTP server to be available over LAN? If that's the case, why not just use SAMBA.
If you want to be able to access/download files remotely, then you WILL need to configure your router to forward the appropriate ports. 
Another alternative, if you want to be able to access files remotely, is to use SSH, then map a virtual drive. This is much more secure and in my opinion simpler. It also enables you to manage your server remotely.

SAMBA even supports windows networks:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by krelkor on 2008-01-03
The BWLOG scripts on my router only allow for ftp backup, not shared drives :(

(i have samba installed for my windows boxes)

---

### Post by spydon on 2008-01-20
Does [ftp://localhost](ftp://localhost) work?

---

