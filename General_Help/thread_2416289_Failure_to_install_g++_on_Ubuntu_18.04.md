---
title: "Failure to install g++ on Ubuntu 18.04"
date: 2019-04-08
forum: General Help
---

### Post by vicroberts on 2019-04-08
I have tried to install g++ on my Ubuntu 18.04 system using sudo atp install g++ but receive this error message:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_4.15.0-45.48_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_4.15.0-45.48_amd64.deb)  404  Not Found [IP: 91.189.91.23 80]

How can I proceed?

Vic Roberts

---

### Post by again? on 2019-04-08
That package version isn't on server.
[ATTACH=CONFIG]282996[/ATTACH]
```

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] lsb_release -d**
Description:	Ubuntu 18.04.2 LTS

**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt policy linux-libc-dev**
linux-libc-dev:
  Installed: 4.15.0-47.50
  Candidate: 4.15.0-47.50
  Version table:
 *** 4.15.0-47.50 500
        500 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages
        500 http://ftp.iinet.net.au/pub/ubuntu bionic-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     4.15.0-20.21 500
        500 http://ftp.iinet.net.au/pub/ubuntu bionic/main amd64 Packages
```

Try updating your apt cache first...
```
sudo apt update
sudo apt install g++
```

---

