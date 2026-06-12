---
title: "[SOLVED] Ubuntu Firewall"
date: 2008-06-19
forum: General Help
---

### Post by javagamer on 2008-06-19
Hi,
   I'm running Hardy Heron and I'm trying to decide which open-source firewall to go with.  I've read a few book on network security so I'd like to be able to access the low-level settings as well as the high level stuff.  Does anyone have any recommendations?

---

### Post by Exsecrabilus on 2008-06-19
[http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html](http://www.ubuntu-unleashed.com/2008/05/howto-take-use-setup-and-advantage-of.html)

---

### Post by Pjotr123 on 2008-06-19
Double post:
[http://ubuntuforums.org/showthread.php?t=834122](http://ubuntuforums.org/showthread.php?t=834122)

Please avoid this in the future.

---

### Post by kpkeerthi on 2008-06-19
Packet filtering capabilities are build into all linux kernels as **Netfilter**. And **iptables**, a tool to configure packet filtering rules, is installed by default in Ubuntu. 

All linux firewalls (including ufw) are just wrappers around netfilter/iptables.

---

### Post by Gannon8 on 2008-06-19
Firestarter is avalable from the respiratory, and it's pretty quiet.

---

### Post by Exsecrabilus on 2008-06-19
> **Pjotr123 said:**
> Double post:
[http://ubuntuforums.org/showthread.php?t=834122](http://ubuntuforums.org/showthread.php?t=834122)

Please avoid this in the future.
LOL, says the backseat moderator.

---

### Post by sdennie on 2008-06-19
I would recommend using UFW.  A good starting guide can be found here: [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw](https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw)

---

### Post by javagamer on 2008-06-19
Thanks for all the help, I think I'll go with Firestarter, it seems to allow you to go as low-level as ufw does, plus it offers high-level controls.

---

### Post by Pjotr123 on 2008-06-19
> **Exsecrabilus said:**
> LOL, says the backseat moderator.

I find this remark offensive and it makes me angry.

Furthermore, I think it's good if we *all* help to keep this forum an agreeable environment. Moderators and ordinary members alike.

---

### Post by Exsecrabilus on 2008-06-19
> **Pjotr123 said:**
> I find this remark offensive and it makes me angry.

Furthermore, I think it's good if we *all* help to keep this forum an agreeable environment. Moderators and ordinary members alike.
Sorry, I was just joking. Chill.

---

