---
title: "Teamviewer crashes after about 5 remote sessions"
date: 2014-11-09
forum: General Help
---

### Post by Slave_to_gadgets on 2014-11-09
I'm new to Lubuntu (or linux in general). Installed Lubuntu 14.10-desktop-i386 on an HP laptop, ran the updates and installed the teamviewer package. all runs fine except after about 5 remote sessions over teamviewer, teamviewer crashes and I cant reconnect. I reboot the machine it connects again fine but happens again after about 5 sessions. 

First of all, where do I find the log files to post?

---

### Post by weatherman2 on 2014-11-09
Teamviewer is a Windows-based program that runs under Wine in Lubuntu (Wine is packaged with it, so self-contained).  The Networking & Wireless forum is probably not the right section for your question to get the best response.

---

### Post by howefield on 2014-11-09
Thread moved to the "*General Help*" forum.

---

### Post by Slave_to_gadgets on 2014-11-09
ok I'll repost in the right place. what section do you recommend?

---

### Post by bapoumba on 2014-11-09
> **Slave_to_gadgets said:**
> ok I'll repost in the right place. what section do you recommend?

No need to repost, Howefield moved your thread for you :)

---

### Post by Slave_to_gadgets on 2014-11-09
Thanks.

---

### Post by Slave_to_gadgets on 2014-11-20
ok not a huge response to this posting.

 Anyway I did find a work around..  wait for it...

It doesn't happen if I drop the connection on the remote computer (by clicking on the X in the lower left Team Viewer session list panel).

Disconnecting your session from the host computer seems to leave it with a bunch of unclosed sessions. 6 or more seems be make Team Viewer on wine/Lubuntu crash and totally loose remote access.

---

