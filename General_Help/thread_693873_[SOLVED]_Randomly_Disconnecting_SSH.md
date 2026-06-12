---
title: "[SOLVED] Randomly Disconnecting SSH"
date: 2008-02-11
forum: General Help
---

### Post by sgardne on 2008-02-11
Hello,

I've recently set up an ubuntu 7.10 server on a vmware server. I'd like to not have to use the vmware infrastructure client to manage the box, so I use ssh. I can get connected fine, but I always get disconnected after about 5-10 minutes (connection reset by peer). Immediately after disconnect, I can not re-connect getting the connection refused error. If I wait a little while, or if I log in with the infrastructure client and do a /etc/init.d/networking restart, It lets me back in. 

I know it's not a problem of me timing out because sometimes it has happened in the middle of typing a command, during a vim session and while reading man pages.

I've looked through a few log files, but I'm not really 100% sure where to look. What log files should I be looking at to see why I'm getting disconnected?

---

### Post by Sokertes on 2008-02-15
In the past I remember something about watchdog in the kernel that causes something similar to what you are talking about.

I ended up recompiling the kernel taking out watchdog (network area) and the problem went away.

I am going off memory here. The watchdog module shuts down the network when no activity, or was it shuts down the server when no network activity. I can't remember. This was back in RedHat 6.0 days

Sokertes

---

### Post by sgardne on 2008-02-15
Thank you for your reply. Actually the problem was that someone on my network was poaching my IP. Once I tracked that down, it went away.

---

### Post by Sokertes on 2008-02-17
I had that happen to me once in an office network. My co-worker told me about doing a tarpit on the offending machine. He told me what it did and how it did it but I can't remember what it was. I do remember that it was very vicious and I do not recommend doing it in an office setting. Only in a home setting where it can be more controlled and there would be no self inflicted consequences. 

hehehe

---

