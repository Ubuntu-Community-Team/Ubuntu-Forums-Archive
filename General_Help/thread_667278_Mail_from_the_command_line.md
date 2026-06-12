---
title: "Mail from the command line"
date: 2008-01-14
forum: General Help
---

### Post by b0rka7a on 2008-01-14
Hi all !
I want to tell me exactly how to configure mutt or other mailing client so I can send mails from the command line.
My idea is to make a script which sends to my e-mail my current IP every time I start my PC.

This is my look of the script:
```
#!/bin/bash
getip=`curl -s www.whatismyip.com/automation/n09230945.asp`
sendip=`echo "Your IP is: $getip"`
mutt my-e-mail@descom.com $sendip
```

---

### Post by Seisen on 2008-01-14
[https://help.ubuntu.com/community/mutt]("https://help.ubuntu.com/community/mutt")

---

### Post by b0rka7a on 2008-01-14
I need to tell me exactly how to send a mail trough the command line (Sorry, but I couldn't find out how :().
Tell me how to configure that SMTP thing, and how to send an e-mail with only one line.

---

