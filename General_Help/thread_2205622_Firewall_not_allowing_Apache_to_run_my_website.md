---
title: "Firewall not allowing Apache to run my website"
date: 2014-02-15
forum: General Help
---

### Post by novice_penguin on 2014-02-15
Hello everyone.  I have been hosting my website on my machine for over 2 years now.  I had to teach myself how to use Apache 2 web server, even though I only know very little about it.  I recently decided to turn on my firewall for security purposes and when I tried to load my website in my web browser, it kept timing out and cannot establish a connection.  When I turn the firewall off, obviously the web site is rendered so now I know for a fact it is the firewall.  I am using the ufw firewall configuration tool that I dl'ed from the software center.  What do I need to do in order for my website to be published again?  Right now the firewall is blocking all incoming and allowing all outgoing and I have not added any rules yet.  I know that's how to fix the problem I'm having, but what do I add to the rule to allow this to happen?  Thanks for any help.

---

### Post by 3rdalbum on 2014-02-15
Allow port 80 incoming. If you have Apache set up to use a different port, then of course allow that port instead.

man ufw

Shows you how to add an ALLOW rule.

---

### Post by novice_penguin on 2014-02-15
Ok so basically the same thing I did with my router.  I had to forward port 80 to get it to publish.   I knew it was simple to fix but I should have known this answer.  Thanks for your help.

---

### Post by 3rdalbum on 2014-02-15
> **novice_penguin said:**
> Ok so basically the same thing I did with my router.  I had to forward port 80 to get it to publish.   I knew it was simple to fix but I should have known this answer.  Thanks for your help.

Well, if you had to forward port 80 on your router, then your router already contains a firewall and you were already protected. You can just turn off UFW as long as you are using that router.

---

