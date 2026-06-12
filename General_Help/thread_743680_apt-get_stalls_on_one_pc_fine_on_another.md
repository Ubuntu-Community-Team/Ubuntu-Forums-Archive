---
title: "apt-get stalls on one pc fine on another"
date: 2008-04-02
forum: General Help
---

### Post by cheeseboy2010 on 2008-04-02
This problem has been haunting me all week. Here's my setup:

router <wireless> wireless bridge <wire> server <wire> my pc

Hope you can read that. The problem is that my pc can download update, install stuff, and surf the internet fine. The server can access the internet fine also, except when downloading updates, it will start strong, then slow down and eventually stop. If I restart apt-get, it will continue for a while then stop. This just started happening when I reinstalled the server. It had run gutsy, and then I reinstalled gutsy. Now it won't work. My pc is running hardy beta. It makes no sense to me. So far I have tried changing repos and disabling ipv6. The only clue I have is that it seems to stop when usng the security.ubuntu.com repo. Has anyone had this happen to them?

EDIT:
I just ran apt-get upgrade and rebooted into a new kernel and it all works fine!

EDIT 2:
Guess I spoke to soon. update worked once, but downloading packages is still slow.

---

### Post by discorsage on 2008-04-03
Can you connect the server directly to your router for a test to verify this isn't some odd networking problem?

---

