---
title: "gftp connection problem to connect to a linux pc (ubuntu) to linux pc (ubuntu)"
date: 2019-02-05
forum: General Help
---

### Post by rajkumar777444 on 2019-02-05
Without enabling firewall GFTP connects to remote PC easily, but GFTP showing error 425 PASV port error while connecting to a linux pc when firewall is on, and using port 21 ftp protocol. Which port should be enabled in firewall to easily connect to linux to linux pc? i even enabled port 20 and 21 ports in vsftpd, but able to connect to windows pc from the linux pc, but not from linux to linux. How it can be solved?

---

### Post by jdeca57 on 2019-02-05
Well I found this about vsftp:
[https://serverfault.com/questions/421161/how-to-configure-vsftpd-to-work-with-passive-mode]("https://serverfault.com/questions/421161/how-to-configure-vsftpd-to-work-with-passive-mode")
And the question why it works with Windows? Probably because that OS is less secure. I may be wrong, of course. ;-)

---

