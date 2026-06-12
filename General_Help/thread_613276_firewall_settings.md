---
title: "firewall settings?"
date: 2007-11-14
forum: General Help
---

### Post by Excalibre on 2007-11-14
I'm not even positive here that I have a problem, but I'm starting to suspect I do. Sometimes, when I get on the web, web pages seem to take an oddly long time to reply when I click links, and this includes huge sites with plenty of infrastructure supporting them (like google). Sometimes images on websites that come from other servers take a weirdly long time to reply. And some sites that appear to be functional when I access them elsewhere just don't seem to be accessible to me. In all cases, when contact is made, downloads are nice and fast; I don't believe there's a problem with my ISP, since this worked right up until my new computer arrived and I switched to Linux.

I know nothing about firewalls and the like, but my understanding is that Ubuntu has some sort of built in firewall. Are its default settings somehow set to be much more secure than Windows, so that perhaps it's causing trouble with HTTP? Or is there some other possibility here? Should I get Firestarter or something? If so, what settings do I use?

---

### Post by scorp123 on 2007-11-14
The firewall is in the Linux kernel and not specific to Ubuntu; because it's in the Linux kernel all distros have it. But per default and unless you defined anything it doesn't do anything.

Guessing from your description of the problem I'd say you have a flaky internet connection  and/or network configuration and this has nothing to do with the Linux firewall.

---

### Post by dpar on 2007-11-14
I doubt that it's a firewall problem, more likely a dns problem.

---

### Post by Giradman on 2007-11-14
> I don't believe there's a problem with my ISP, since this worked right up until my new computer arrived and I switched to Linux.

First, you might want to provide some more information on the quote above - type of new computer (NIC card) - assume had a Windows OS?  How did you switch to Linux - any installation problems?

Concerning the Linux firewall, you're certainly right that it is part of the OS (based on iptables & quite robust apparently from my reading) - I installed Firestarter, which will permit you to regulate the inbound/outbound traffic - does not stay 'open', just used for adjusting the internal firewall - but I'd probably be more concerned initially w/ other issues mentioned above - good luck!  :)

---

### Post by Excalibre on 2007-11-14
> **dpar said:**
> I doubt that it's a firewall problem, more likely a dns problem.
Actually, yeah, that does sound reasonable. Is there some reason my operating system might interfere with DNS lookup? It doesn't seem to me like it should make any difference at all. Or is it possible some hardware issue could interfere with DNS results? That seems unlikely. It's possible, I suppose, that there's some problem with my ISP that began at the same time I got the new computer, but it seems unlikely (I haven't used the other computer on our home network enough to notice.)


> **Giradman said:**
> First, you might want to provide some more information on the quote above - type of new computer (NIC card) - assume had a Windows OS?  How did you switch to Linux - any installation problems?

Concerning the Linux firewall, you're certainly right that it is part of the OS (based on iptables & quite robust apparently from my reading) - I installed Firestarter, which will permit you to regulate the inbound/outbound traffic - does not stay 'open', just used for adjusting the internal firewall - but I'd probably be more concerned initially w/ other issues mentioned above - good luck!  :)
The computer is a Dell Optiplex 755; the chipset is Intel Q35 Express and it has an integrated NIC. I'm not having any trouble with connection speeds or anything, just with initiating a connection to another computer. I haven't booted it into Windows except after I installed some hardware (more memory, a video card, and a second hard drive) right after getting it, so I'm not sure whether or not this problem exists in Windows.

The computer itself is behind a home network so we can share the internet connection; I never had any problems relating to that before, however - so it doesn't seem likely that it's a router setting issue. But as I've probably made very clear, I don't really know much about this stuff. :)

---

### Post by AlexThomson_NZ on 2007-11-14
If your router does not support IPv6, and IPv6 is enabled in FF, it will wait for this to fail (timeout) before trying IPv4.  Open "about:config" in FF, filter for IPv6, you should get "network.dns.disableIPv6", make sure this is "true"

---

### Post by Excalibre on 2007-11-14
> **AlexThomson_NZ said:**
> If your router does not support IPv6, and IPv6 is enabled in FF, it will wait for this to fail (timeout) before trying IPv4.  Open "about:config" in FF, filter for IPv6, you should get "network.dns.disableIPv6", make sure this is "true"
Okay, thanks, I'll try that.

---

### Post by ramjet_1953 on 2007-11-15
I found a performance increase when surfing, by putting the two opendns ip addresses in my ADSL router.

Check it out here: [http://www.opendns.com/](http://www.opendns.com/)

Regards,
Roger :cool:

---

