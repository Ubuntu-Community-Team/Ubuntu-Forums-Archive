---
title: "Samba4 Install Confusion"
date: 2013-08-23
forum: General Help
---

### Post by john65 on 2013-08-23
I'm sure that I can't be the only person who's experienced this, but I can find no reference anywhere to the issue.
 
 I've tried over an extended time to install Samba4 on Ubuntu1304.  I can happily do so by building it from source - it works just fine this way.  However, I'd really rather use the standard packages, because that way I don't have to worry about upgrading it myself - the usual mechanisms will do it for me.
 
 However, when I try to install the samba4 packages (samba4 and samba4-clients) I run into a problem.  THe samba4 package installs OK, and reports itself (via samba -V) as version4.  However, smbclient (via smbcleint -V) reports itself as v3.6.9 and doesn't interoperate correctly.  I've checked that there aren't any samba packages installed before I start (dpkg --get-selecitons | grep samba), no sign there.
 
 As I said, I can't believe I'm the only one who's had this problem.  What am I missing ?
 
 Thanks

---

### Post by JnPson on 2013-09-08
I have this problem on my Samba 4.0.9 server.
```
root@dc01:/samba-master# cd /
root@dc01:/# samba -V
Version 4.0.9
root@dc01:/# smbclient -V
Version 3.6.3

```

Is there a way to just upgrade smbclient? Or any other way to fix this?

---

### Post by MikeEvans on 2013-12-30
The client is renamed to smbclient4

---

