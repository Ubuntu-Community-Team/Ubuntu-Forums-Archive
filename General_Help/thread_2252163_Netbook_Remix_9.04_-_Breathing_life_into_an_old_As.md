---
title: "Netbook Remix 9.04 - Breathing life into an old Asus Eee PC"
date: 2014-11-09
forum: General Help
---

### Post by moebob24 on 2014-11-09
So,

One old netbook - one potential IRC box. Only issue is this thing won't sudo apt-get update so I can't install ssh server.

Advice?

---

### Post by llamabr on 2014-11-09
Yes, so just copypaste your input, and any error you get.  We'll be able to help debug it for you.

---

### Post by moebob24 on 2014-11-09
```
Ign http://security.ubuntu.com jaunty-security Release.gpg
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security Release
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com jaunty Release
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates Release
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://security.ubuntu.com jaunty-security/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://security.ubuntu.com jaunty-security/restricted Packages
Ign http://security.ubuntu.com jaunty-security/main Sources
Ign http://security.ubuntu.com jaunty-security/restricted Sources
Ign http://security.ubuntu.com jaunty-security/universe Packages
Ign http://security.ubuntu.com jaunty-security/universe Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/main Packages
Ign http://us.archive.ubuntu.com jaunty/restricted Packages
Ign http://us.archive.ubuntu.com jaunty/main Sources
Ign http://security.ubuntu.com jaunty-security/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty/restricted Sources
Ign http://us.archive.ubuntu.com jaunty/universe Packages
Ign http://us.archive.ubuntu.com jaunty/universe Sources
Ign http://us.archive.ubuntu.com jaunty/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty/multiverse Sources
Ign http://us.archive.ubuntu.com jaunty-updates/main Packages
Err http://security.ubuntu.com jaunty-security/main Packages
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://security.ubuntu.com jaunty-security/restricted Packages
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://security.ubuntu.com jaunty-security/main Sources
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://security.ubuntu.com jaunty-security/restricted Sources
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://security.ubuntu.com jaunty-security/universe Packages
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://security.ubuntu.com jaunty-security/universe Sources
  404 Not Found [IP: 2001:67c:1562::14 80]
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://us.archive.ubuntu.com jaunty-updates/main Sources
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://us.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://us.archive.ubuntu.com jaunty-updates/universe Sources
Err http://security.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found [IP: 2001:67c:1562::14 80]
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Err http://us.archive.ubuntu.com jaunty/main Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/restricted Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/main Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/restricted Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/universe Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/universe Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://security.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found [IP: 2001:67c:1562::14 80]
Err http://us.archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found [IP: 2001:67c:1562::16 80]
Err http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found [IP: 2001:67c:1562::16 80]
```

---

### Post by sports fan Matt on 2014-11-09
Jaunty is EOL...Could you try downloading a Precise 12.04 or Trusty 14.04 iso?

---

### Post by moebob24 on 2014-11-09
> **sports fan Matt said:**
> Jaunty is EOL...Could you try downloading a Precise 12.04 or Trusty 14.04 iso?

Will that run on this?

---

### Post by cbraxton on 2014-11-09
I'm running 32-bit Xubuntu 14.04 on an old Asus 1000HA netbook and it runs OK. (This particular netbook has 2GB memory and an SSD. If you have less memory you might want to try Lubuntu instead.)

---

### Post by cbraxton on 2014-11-09
I'm running 32-bit Xubuntu 14.04 on an old Asus Eee 1000HA netbook and it runs OK, a little sluggish but not real bad. (This particular netbook has 2GB memory and an SSD. If you have less memory you might want to try Lubuntu instead.)

---

### Post by cbraxton on 2014-11-09
I'm running 32-bit Xubuntu 14.04 on an old Asus Eee 1000HA netbook and it runs OK, a little sluggish but not real bad. (This particular netbook has 2GB memory and an SSD. If you have less memory you might want to try Lubuntu instead.)

---

### Post by moebob24 on 2014-11-09
> **cbraxton said:**
> I'm running 32-bit Xubuntu 14.04 on an old Asus Eee 1000HA netbook and it runs OK, a little sluggish but not real bad. (This particular netbook has 2GB memory and an SSD. If you have less memory you might want to try Lubuntu instead.)

Hmm, I think I'll give it a try with Lubuntu just for performance reasons. I really only want a couple of things running on this thing.

Thanks.

---

### Post by moebob24 on 2014-11-10
Now running Lubuntu 14.10 :D

Thanks guys!

---

