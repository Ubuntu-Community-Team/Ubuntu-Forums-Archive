---
title: "Slow internet with server running"
date: 2007-05-17
forum: General Help
---

### Post by xotsegox on 2007-05-17
I'm running Ubuntu 6 Desktop on my spare computer. It has a 3Com (I believe) 10/100 NIC in it. It's a cheap eMachine with a 900Mhz Celeron. I also have Apache set up on it. I have a 3MB down/200k up cable connection. I have a Linksys WRT54G router and a Linksys cable modem. I have port 80 forwarded to my "server" (Ubuntu) machine. I previously ran a Windows Server OS and had this same problem. Ubuntu is a bit faster (with the HTTP server), but after about 20 minutes of the server being ON, my internet literally DIES. It took my room mate 10 minutes to get a failed attempt to log into Yahoo! Messenger on his computer. My speed becomes slower than 56K. As I said, this happens with Ubuntu AND Windows. Strange thing is, it didn't seem to happen at all when I was running IIS 5.0 on Windows XP, but as we all know, Windows XP doesn't allow unlimited connections. Someone, please help!

---

### Post by heimo on 2007-05-17
Does the WRT54G have original firmware? Never updated? I'd flash it with latest firmware from Linksys - or perhaps OpenWRT. I remember reading about some stability issues with this particular router.

---

