---
title: "filezilla ftp error"
date: 2014-07-03
forum: General Help
---

### Post by sniper8752 on 2014-07-03
I am trying to connect to my FTP server on my Linux machine, and get this error:
500 OOPS: vsftpd: refusing to run with writable root inside chroot()

What does this mean?

---

### Post by slickymaster on 2014-07-03
There's a [bug report on vsftpd 2.3.5-3 version]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=735191#10") which seems to be solved in vsftpd version 3. If you're running that version try to update it.

---

### Post by sniper8752 on 2014-07-03
Is there a way to "update" a program?  Or should I just un-install, and re-install?

---

### Post by slickymaster on 2014-07-03
> **sniper8752 said:**
> Is there a way to "update" a program?  Or should I just un-install, and re-install?

In this particular case I'm unaware of any process to upgrade vsftpd version, so if I were you I would opt for your second option.

---

### Post by sniper8752 on 2014-07-03
when I try to "make", it gives me an error about an "undefined reference to 'crypt'".  How do I install this vsftpd?  I have it downloaded, and un-zipped.

---

### Post by slickymaster on 2014-07-03
Why don't you install via atp-get?
I believe the latest vsftpd release is v3.0.2```
sudo apt-get install vsftpd
```See [this]("https://help.ubuntu.com/community/vsftpd").

---

