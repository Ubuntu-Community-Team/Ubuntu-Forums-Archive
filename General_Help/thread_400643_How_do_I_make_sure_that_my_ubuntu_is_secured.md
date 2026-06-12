---
title: "How do I make sure that my ubuntu is secured?"
date: 2007-04-03
forum: General Help
---

### Post by kpkeerthi on 2007-04-03
I'm not asking about a virus or a spyware scanner but rather interested in knowing the measures I should take to keep my ubuntu secured. What tools do you suggest to make sure that I'm not hacked or my ubuntu is not making unsolicited inbound or outbound connections?

---

### Post by kidders on 2007-04-03
Hi there,

You *could* argue that taking any security precautions at all with Linux requires a certain degree of paranoia. The question, though, is how paranoid you need to be! What kind of system are you running?

Very briefly...[LIST]
[*] All users must be _meticulous_ with their filesystem permissions management. Linux will slam-dunk you mercilessly if you make even a small mistake.
[*] No user should *ever* install an application from an unsigned or unfamiliar source.
[*] From a networking perspective, personal home computer users should probably run a firewall, although doing anything in any way special with it would usually be overkill.
[*] Home users should also avoid picking obvious usernames, low-quality passwords, or setting a root password.
[*] Higher risk users (such as those with lots of accounts on their systems) should only install apps from the official Ubuntu repositories, install intrusion detection, and conduct regular permissions audits.
[*] On servers, anti-virus software (chiefly for the protection of *other* computers), anti-spam software, proxies and hardened firewalls are worth considering.
[*] Never install non-release versions of any software on mission critical system.[/LIST]To answer your questions more directly though...

Technically, incoming connections are always unsolicited. One can only be created if you explicitly configure Ubuntu to listen for them. Outgoing connections can be most easily limited by firewalls & proxies. Detecting malicious hacks can be done relatively reliably with intrusion detection software. If one of those gets set off (being mindful of false positives, of course), I would very seriously consider reinstalling my OS though.

---

### Post by gerrymoth on 2007-04-04
Could/Would you recommend any Anti-Spam or Intrusion Detection software?

I have installed Ubuntu 6.10, then upgraded to Fesity 7.04. I've installed Firstarter and Avast (wondering if I should have installed ClamAV?), but looking for a recommended Anti-Spam/Anti-Spyware software. 

> **kidders said:**
> Hi there,

You *could* argue that taking any security precautions at all with Linux requires a certain degree of paranoia. The question, though, is how paranoid you need to be! What kind of system are you running?

Very briefly...[LIST]
[*] All users must be _meticulous_ with their filesystem permissions management. Linux will slam-dunk you mercilessly if you make even a small mistake.
[*] No user should *ever* install an application from an unsigned or unfamiliar source.
[*] From a networking perspective, personal home computer users should probably run a firewall, although doing anything in any way special with it would usually be overkill.
[*] Home users should also avoid picking obvious usernames, low-quality passwords, or setting a root password.
[*] Higher risk users (such as those with lots of accounts on their systems) should only install apps from the official Ubuntu repositories, install intrusion detection, and conduct regular permissions audits.
[*] On servers, anti-virus software (chiefly for the protection of *other* computers), anti-spam software, proxies and hardened firewalls are worth considering.
[*] Never install non-release versions of any software on mission critical system.[/LIST]To answer your questions more directly though...

Technically, incoming connections are always unsolicited. One can only be created if you explicitly configure Ubuntu to listen for them. Outgoing connections can be most easily limited by firewalls & proxies. Detecting malicious hacks can be done relatively reliably with intrusion detection software. If one of those gets set off (being mindful of false positives, of course), I would very seriously consider reinstalling my OS though.

---

### Post by az on 2007-04-04
> **kpkeerthi said:**
> I'm not asking about a virus or a spyware scanner but rather interested in knowing the measures I should take to keep my ubuntu secured. What tools do you suggest to make sure that I'm not hacked or my ubuntu is not making unsolicited inbound or outbound connections?

1.  Keep up-to-date with software updates.

2.  Do not install any software from non-ubuntu repositories.

---

### Post by xopher on 2007-04-04
And you probably don't need an antivirus program for your linux system, only if you wan't to scan other systems (READ) windows based. ;)

---

