---
title: "Limit pure-ftp signin attempts?"
date: 2012-12-07
forum: General Help
---

### Post by LuniTux on 2012-12-07
Hello,

I have an ftp server using pureftp. I noticed that the server gets hundred of attempts a day like this one:

```

Dec  2 23:25:14 ftp_server_name pure-ftpd: (?@60.211.252.98) [INFO] New connection from 60.211.252.98
Dec  2 23:25:19 ftp_server_name pure-ftpd: (?@60.211.252.98) [WARNING] Authentication failed for user [Administrador]
Dec  2 23:26:21 ftp_server_name pure-ftpd: last message repeated 4 times

```

Is there a way that I can block the IP address that is attempting to sign in for a set amount of time if they fail to sign in X amount of times?

Thanks,

---

### Post by LuniTux on 2012-12-07
I found a solution:

[http://itswapshop.com/.../how-install-and-configure-fail2ban...]("http://itswapshop.com/content/how-install-and-configure-fail2ban-ubuntu-1004-ssh-and-pure-ftpd")

---

### Post by LuniTux on 2012-12-07
Typed too soon...

I tested fail2ban on a computer with **iptables**, but the server that needs the program is using **ufw**. I found how to setup ssh and other programs such as ssh but not ftp. Any help would be appreciated.

fail2ban/jail.conf
```
...
[pureftpd]

enabled  = true
port	 = ftp,ftp-data,ftps,ftps-data
filter   = pure-ftpd
logpath  = /var/log/messages
maxretry = 4
...
```

---

