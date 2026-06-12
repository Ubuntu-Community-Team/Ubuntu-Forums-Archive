---
title: "Exim not receiving mail"
date: 2014-11-02
forum: General Help
---

### Post by mrkirby153 on 2014-11-02
Hello,

I was checking my domains over at [http://mxtoolbox.com](http://mxtoolbox.com) and it said that in terms of SMTP, it was getting a failed to connect. I have verified that port 25 is open and exim4 is listening on it. ```
Active Internet connections (only servers)Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:32000         0.0.0.0:*               LISTEN      7510/java
tcp        0      0 0.0.0.0:39363           0.0.0.0:*               LISTEN      7510/java
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      19108/mysqld
tcp        0      0 0.0.0.0:8080            0.0.0.0:*               LISTEN      7510/java
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      5298/apache2
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      26062/vsftpd
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      306/sshd
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4177/exim4
tcp6       0      0 :::22                   :::*                    LISTEN      306/sshd



```

Port 25 is also open on my firewall.

---

### Post by lisati on 2014-11-02
Do you have port forwarding for port 25 set up on your router?

---

### Post by mrkirby153 on 2014-11-02
Pretty sure I do. It's a hosted vps and everything else works fine (ssh, ftp, html)

---

### Post by mrkirby153 on 2014-11-02
One of the problems was that exim wasn't listening on all network adaptors. I fixed that, now gmail won't send emails to my server. I have it forwarding to my personal email address and it never gets sent. Do I need my server to support TLS?

---

