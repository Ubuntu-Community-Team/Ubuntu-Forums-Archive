---
title: "vsftpd error &quot;500 Illegal PORT command.&quot;"
date: 2020-02-01
forum: General Help
---

### Post by charkel2 on 2020-02-01
I am trying to connect to my vsftpd server using PotPlayer. For some reason PotPlayer is sending command 
```
PORT 192,168,1,2,223,152
AND
LPRT 6,16,0,0,0,0,0,0,0,0,0,0,0,$

```
Which makes the connection fail. And there is no setting for stopping this in PotPlayer.

Here is the full connection log fro vsftpd.conf
```
$Sat Feb  1 22:55:45 2020 [pid 28103] CONNECT: Client "xxx.xxx.xxx.xxx"
Sat Feb  1 22:55:45 2020 [pid 28103] FTP response: Client "xxx.xxx.xxx.xxx", "220 (vsFTPd 3.0.3)"
Sat Feb  1 22:55:45 2020 [pid 28103] FTP command: Client "xxx.xxx.xxx.xxx", "USER charkel"
Sat Feb  1 22:55:45 2020 [pid 28103] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "331 Please specify the password$
Sat Feb  1 22:55:45 2020 [pid 28103] [charkel] FTP command: Client "xxx.xxx.xxx.xxx", "PASS <password>"
Sat Feb  1 22:55:45 2020 [pid 28101] [charkel] OK LOGIN: Client "xxx.xxx.xxx.xxx"
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "230 Login successful."
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP command: Client "xxx.xxx.xxx.xxx", "CWD /"
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "250 Directory successfully chan$
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP command: Client "xxx.xxx.xxx.xxx", "TYPE A"
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "200 Switching to ASCII mode."
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP command: Client "xxx.xxx.xxx.xxx", "PORT 192,168,1,2,224,67"
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "500 Illegal PORT command."
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP command: Client "xxx.xxx.xxx.xxx", "LPRT 6,16,0,0,0,0,0,0,0,0,0,0,0,$
Sat Feb  1 22:55:45 2020 [pid 28105] [charkel] FTP response: Client "xxx.xxx.xxx.xxx", "500 Unknown command."

```


Any ideas on how to solve this?

---

