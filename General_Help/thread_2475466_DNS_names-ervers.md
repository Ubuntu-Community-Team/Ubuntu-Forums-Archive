---
title: "DNS names-ervers"
date: 2022-05-28
forum: General Help
---

### Post by jacksonguitars on 2022-05-28
Dear sirs and ladies! 

Is there any way of preventing DNS changes for anyone not being sudo user?

Thank you!

Best regards
JacksonG

---

### Post by TheFu on 2022-05-28
Don't use DHCP.  Manually force the exact DNS you want and perhaps setup an outbound firewall rule to redirect any 53/UDP or 53/tcp outbound requests to the DNS you prefer.  In 22.04, iptables has been replaced by nftables, so the exact firewall rule needed could have changed. It is important to know when searching for answers.

But the first step is to stop using DHCP ... or you control the DHCP settings and force the DNS servers you prefer in those settings.

---

### Post by HermanAB on 2022-05-28
You can control things better in your gateway router.

---

### Post by jacksonguitars on 2022-05-29
How about editing resolv.conf in such a way that only su can make changes using chattr ? Will that prevent UI changes?

---

### Post by TheFu on 2022-05-29
> **jacksonguitars said:**
> How about editing resolv.conf in such a way that only su can make changes using chattr ? Will that prevent UI changes?

Perhaps.  

Removing systemd-resolved and resolvconf first, then ensuring /etc/resolv.conf isn't a symlink would be needed first.  

I used to do this before I started "masking" systemd-resolved and resolvconf.  I'm not much of a GUI user, so how this impacts any GUI network tools is unknown to me.  I purge network-manager from my systems too after becoming tired of fighting with it.  

My network needs are more complex than most users.

If the /etc/resolv.conf has a primary and backup DNS listed and cannot be modified, then that's all most systems need.  It becomes murky when we want that to be automatically managed via DHCP if it is a laptop.  For desktops with static network configurations, all that extra complexity just gets in the way.

Also, this will impact DNSSEC or DNS-over-HTTPS, if those are planned.

---

### Post by ActionParsnip on 2022-05-29
Just make everyone else not in the sudo group and leave the root account locked. You will then be the administrator and the rest will only be users

---

### Post by jacksonguitars on 2022-05-30
This is the way to go. If non-sudo users cannot use the network-manager. 

Thank you, for your help. And thank you all.

---

### Post by TheFu on 2022-05-30
> **jacksonguitars said:**
> This is the way to go. If non-sudo users cannot use the network-manager. 

Thank you, for your help. And thank you all.

Whether that is true depends on how the networking was installed.  There is system-level and user-level.  If the networking is up BEFORE any user logs in, then that implies system-level network control.  Typically, this isn't used on laptops or wifi-connected systems.

---

