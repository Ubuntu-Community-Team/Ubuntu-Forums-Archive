---
title: "Auth.log not getting updated ??"
date: 2007-02-15
forum: General Help
---

### Post by DarkAngel88 on 2007-02-15
Good day !

I'm having a small problem on my server.  I'm using fail2ban for blocking scripts and bots from trying to get access to my server (via ssh) using dictionary attacks.  Blocking ip for my ftp server works well but when trying to block ips from ssh, it doesn't work sometimes.

The reason why I say "sometimes" is that when I reboot the server, it works.  But after a while, it stops working.  I checked my auth.log located in "/var/log/auth.log" and I don't see any logged infos.  Even if I try to log in, I can but I won't see my successful login in auth.log.  So fail2ban works well but I'm wondering if a CRON job is updating auth.log or it's supposed to do it by itself ?

Can anyone help me on this ?  

Sorry for my English ... not my native language !

---

### Post by DarkAngel88 on 2007-02-15
Hi again,

I just found out that if I restart sysklogd I was able to get data in auth.log as usual.  Still, I doubt that will work normally and I still think something is wrong.

If you have an idea, don't hesitate !

Thanks !

---

