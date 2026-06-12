---
title: "MY IP address conbtacting my Web site"
date: 2007-10-13
forum: General Help
---

### Post by LeeU on 2007-10-13
I have an interesting problem. It seems that my laptop (running Feisty 7.04) attempts to contact my Web site at various times using my IP number (I use Road Runner). When I check to see what my IP is, it's the same as the IP address that is trying to access my Web site (but they're generally pages with addresses like /mysqladmin/main.php - I don't have any pages like that). It only seems to happen when my laptop is on.

Does anybody have any idea what is happening (I'm a Linux nube)?

---

### Post by Nesman on 2007-10-13
Have you assigned a domain to your laptop in the network settings?  It's possible that if you used your website address as your network domain that requests to unknown servers would default to your domain, or something like that.  (It's been a while since I've been in that situation, so I can't really remember what my symptoms were)

If this is the case, test it by trying to access addresses like foo/bar.html and see where you end up.

---

### Post by LeeU on 2007-10-14
I have XAMPP set-up but it isn't running when this happens. My network settings show the local domain I set-up for XAMPP but, again, the Apache server in XAMPP isn't running when this happens.

---

