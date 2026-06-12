---
title: "Help with failregex fail2ban"
date: 2016-03-16
forum: General Help
---

### Post by gustavo25 on 2016-03-16
Hello,

I am trying to create the regular expression , but I have difficulties through of the log above:

2016-03-16 04:20:01,862 - [  10975000] ************ New connection from: 52.29.2.57
2016-03-16 04:20:02,026 - [  10975000] C --> EHLO ylmf-pc
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-mail.domain.com
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-SIZE 20480000
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-VRFY
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-ETRN
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-AUTH PLAIN LOGIN
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-AUTH=PLAIN LOGIN
2016-03-16 04:20:02,027 - [  10975000] S <-- 250-ENHANCEDSTATUSCODES
2016-03-16 04:20:02,027 - [  10975000] S <-- 250 DSN
2016-03-16 04:20:02,190 - [  10975000] C --> AUTH LOGIN
2016-03-16 04:20:02,190 - [  10975000] S <-- 334 VXNlcm5hbWU6
2016-03-16 04:20:02,354 - [  10975000] C --> YnJ1bm8ubWlyYW5kYQ==
2016-03-16 04:20:02,354 - [  10975000] S <-- 334 UGFzc3dvcmQ6
2016-03-16 04:20:02,517 - [  10975000] C --> YnJ1bm8ubWlyYW5kYTg4OA==
2016-03-16 04:20:02,581 - [  10975000] S <-- 535 5.7.8 Error: authentication failed: authentication failure


I would like to capture the IP of the first line, when I receive the message of the last line "535 5.7.8 Error: authentication failed: authentication failure".

---

