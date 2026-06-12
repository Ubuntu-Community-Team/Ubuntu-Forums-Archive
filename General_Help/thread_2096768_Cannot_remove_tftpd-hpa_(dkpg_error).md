---
title: "Cannot remove tftpd-hpa (dkpg error)"
date: 2012-12-20
forum: General Help
---

### Post by redox000 on 2012-12-20
I tried installing tftpd-hpa. I couldn't get it to work (same issue as my other thread [here]("http://ubuntuforums.org/showthread.php?p=12414822#post12414822")), so I tried to uninstall it using sudo apt-get remove. However, I got an error on the uninstall and now it's stuck in limbo. I can't install it again, I can't uninstall it, and I can't install another tftp server. Here is the error I get:

```
dkpg: error processing tftpd-hpa (--configure):
 package tftpd-hpa is not ready for configuration
 cannot configure (current status 'half-installed')
Errors were encountered while processing:
 tftpd-hpa
```

---

### Post by redox000 on 2012-12-21
Solved it. I removed the tftpd-hpa config file at /etc/default/tftpd-hpa and ran the apt-get remove command again and it worked.

---

