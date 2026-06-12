---
title: "Update command does not work"
date: 2014-07-23
forum: General Help
---

### Post by ola4eva on 2014-07-23
Hello friends,

Please i have tried several times to update both Ubuntu 12.10 desktop version and 13.04 server version without any success.
Each time i tried to run sudo apt-get update or sudo apt-get upgrade the following errors always returns. 

Err [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) raring/universe fail2ban all 0.8.7.1-1
  404  Not Found [IP: 91.189.88.153 80]
Err [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) raring/main python-pyinotify all 0.9.3-1.1ubuntu1
  404  Not Found [IP: 91.189.88.153 80]
Err [http://ng.archive.ubuntu.com/ubuntu/](http://ng.archive.ubuntu.com/ubuntu/) raring/main whois amd64 5.0.20ubuntu1
  404  Not Found [IP: 91.189.88.153 80]
Err [http://lt.archive.ubuntu.com/ubuntu/](http://lt.archive.ubuntu.com/ubuntu/) raring/universe fail2ban all 0.8.7.1-1
  404  Not Found [IP: 193.219.61.87 80]
Failed to fetch [http://lt.archive.ubuntu.com/ubuntu/pool/universe/f/fail2ban/fail2ban_0.8.7.1-1_all.deb](http://lt.archive.ubuntu.com/ubuntu/pool/universe/f/fail2ban/fail2ban_0.8.7.1-1_all.deb)  404  Not Found [IP: 193.219.61.87 80]
Failed to fetch [http://ng.archive.ubuntu.com/ubuntu/pool/main/p/pyinotify/python-pyinotify_0.9.3-1.1ubuntu1_all.deb](http://ng.archive.ubuntu.com/ubuntu/pool/main/p/pyinotify/python-pyinotify_0.9.3-1.1ubuntu1_all.deb)  404  Not Found [IP: 91.189.88.153 80]
Failed to fetch [http://ng.archive.ubuntu.com/ubuntu/pool/main/w/whois/whois_5.0.20ubuntu1_amd64.deb](http://ng.archive.ubuntu.com/ubuntu/pool/main/w/whois/whois_5.0.20ubuntu1_amd64.deb)  404  Not Found [IP: 91.189.88.153 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Please what am I doing wrong?

Thanks

---

### Post by slickymaster on 2014-07-23
Moved to the **General Help** sub-forum.

---

### Post by ibjsb4 on 2014-07-23
You have waited too long. 12.10 and 13.04 have both reached end of life and no longer supported.  Thus the errors.

Time for a fresh install.

---

### Post by slickymaster on 2014-07-23
Raring Ringtail End of Life was reached on January 27, 2014, and as a result of that it stopped receiving security updates, bug fixes or package upgrades from the main Ubuntu repositories.

I would advise you to backup all you important data and either upgrade your system to 14.04 or make a clean install of 14.04.

---

### Post by Bucky Ball on 2014-07-23
*Thread closed.*

Welcome. You are trying old and unsupported releases, and in keeping with slickymaster's last post, please upgrade to a supported release and post a new thread with any issues as we no longer provide support for EOL releases here. See here for staff recommendations on EOL releases:

[http://ubuntuforums.org/showthread.php?t=2229730&highlight=staff+recommendations+eol](http://ubuntuforums.org/showthread.php?t=2229730&highlight=staff+recommendations+eol)

In the releases you are currently using, no, the update command will not work. The repositiories are no longer active. 

Good luck.

---

