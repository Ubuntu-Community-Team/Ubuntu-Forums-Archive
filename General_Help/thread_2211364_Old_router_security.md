---
title: "Old router security"
date: 2014-03-15
forum: General Help
---

### Post by maglin2 on 2014-03-15
Hello,
This isn't really an Ubuntu question, but I thought I'd try it here and hope you'll indulge me.

I have a very old router (NETGEAR DG834G) that is no longer supported - it just keeps working so I've never seen any need to change it. 

I have changed the default password, UPnP is diabled, and Remote Management is disabled (and always has been).

I have read recently that old routers whose software cannot be upgraded are vulnerable to malware. Can anyone advise if this is really an issue for me? Do I need a new router, or is this perhaps just a marketing ruse by router manufacturers?

(I also run UFW with default settings, if that is at all relevant).

Many thanks
Dave

---

### Post by Lars Noodén on 2014-03-15
Can you upgrade the firmware on it to DD-WRT, OpenWRT or Tomato?

---

### Post by Sef on 2014-03-15
> [COLOR=#000000]I have read recently that old routers whose software cannot be upgraded are vulnerable to malware. Can anyone advise if this is really an issue for me? Do I need a new router, or is this perhaps just a marketing ruse by router manufacturers?[/COLOR]

Yes, you are vulnerable, but how vulnerable is the question. 1) If one goes to dodgy sites, porn sites, or other sites that are kno wn for having malware, one's chances of getting a virus are increased. 2) So how secure do you like to be? If you like to like more risk, then keeping your current router is fine, but if you prefer less risk, then getting a new router would be best.  

> [COLOR=#000000][FONT=Arial]they're coming to take my data away, ha, ha[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]They're coming to take my data away, ho, ho, hee, hee, ha, ha*[/FONT][/COLOR]

*with apologies to [Napoleon XIV]("https://www.youtube.com/watch?v=hnzHtm1jhL4")

---

### Post by 3rdalbum on 2014-03-15
In theory, an old router would be no less secure than a new one. Routers only perform very basic functions - transferring data - and nothing an attacker does would affect the router itself.

However that is only theory. In reality, router manufacturers have implemented dumb features or implemented good features badly, introducing horrible security problems. Your router might have one of those problems that was fixed in a later version.

Unfortunately, you don't know whether your router is completely free of insecure features and whether the new router might have them instead. No way of telling!

In short... Damned if you do and damned if you don't. Keep the old one unless you know of a specific flaw.

---

### Post by maglin2 on 2014-03-16
Thanks for the replies.

I am actually now no longer sure if my router is unsupported. It is a Netgear DG834Gv3, with firmware v4.01.40. It is about 8 years old, and I last upgraded the firmware about 4 years ago.

From looking at the Netgear support site, that, though very old, is the latest firmware for this model for Europe (there looks to be something later for North America). It doesn't actually say the router is now unsupported (except, oddly, on the Italian site).

(I got the impression it was unsupported from my previous ISP - but of course they had a new one to send me to try to keep my business, and so perhaps had a motive to say this - but maybe I am being too cynical there).

In response to Lars Nooden, DD-WRT and Tomato don't seem compatible with this hardware. OpenWRT may be - but it looks tricksy.

I do actually have a newer router from my current ISP - but I stopped using that because it wouldn't let me specify DNS, had a couple of permanently open ports that I couldn't close, and apparently suffered from the WPS vulnerability that cropped up a few years back.

---

