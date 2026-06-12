---
title: "PS3 Media Server"
date: 2012-11-08
forum: General Help
---

### Post by hilts01 on 2012-11-08
After tinkering with PS3 Media Server on the peppemint 3 distro just recently and seeing all the reports of the big red cross and all the 'no renerder connected' calls for help. I think ive found the culprit (or 1 of them anyway!) 
 
For me, it was about opening the correct firewall ports from a terminal. So I open a terminal as root: 'ctrl-alt-T' then type 'sudo bash' then pwd, then enter
 
[FONT=monospace]iptables -I INPUT -p tcp --dport 5001 --syn -j ACCEPT[/FONT]
 
 
Restart the server & bingo! connected - big green tick - hurray!
 
However, each time i switch off my PC then boot up later on, I have to follow this same procedure? 
 
How can i write somthing into the bootup that opens this port on each reboot?

---

### Post by dannyboy79 on 2012-11-08
here's one way

[http://www.debian-administration.org/articles/445](http://www.debian-administration.org/articles/445)

---

