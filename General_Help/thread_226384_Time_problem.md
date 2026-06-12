---
title: "Time problem"
date: 2006-07-31
forum: General Help
---

### Post by seshomaru samma on 2006-07-31
Today is July 31st but my Ubuntu says its August 1st on the left hand side of thetop panel
So I clicked on it and changed it to July 31st but:

Look what happens when I use sudo:
```
sesho@ubuntu:~$ sudo ls
sudo: timestamp too far in the future: Jul 31 22:27:26 2006
```

Now I'm forced to change it back to August 1st
I don't want to live in the future ....I'm very conservative;-)

---

### Post by zxee on 2006-07-31
Are you dual booting? Sometimes this happens because the primary system's time is set incorrectly. Also the systems are out of sync i.e one set to utc another to local time.
If you continue to have problems there is a set_nist_time script available for setting time  [http://www.zdo.com](http://www.zdo.com)
[ftp://hun.ece.drexel.edu/pub/cinar/nist*](ftp://hun.ece.drexel.edu/pub/cinar/nist*)
[ftp://ftp.cpan.org/pub/CPAN/authors/id/A/AO/AOCINAR/nist*](ftp://ftp.cpan.org/pub/CPAN/authors/id/A/AO/AOCINAR/nist*)   [ftp://sunsite.unc.edu/pub/Linux/system/admin/timei/nist*](ftp://sunsite.unc.edu/pub/Linux/system/admin/timei/nist*)

---

### Post by seshomaru samma on 2006-08-02
It's sorted now
I am dual booting
I solved it by going to the time and date setting and clicked 'synchronise now'

---

