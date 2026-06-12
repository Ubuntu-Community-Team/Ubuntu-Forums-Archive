---
title: "voip connections"
date: 2016-11-28
forum: General Help
---

### Post by jgw on 2016-11-28
I am considering switching my landline to voip.  I also want to use my existing phone system.  My thought was magic jack.  Problem is that it will not work with linux.  I am looking for a voip system that will allow me to connect to my existing phones.   Anybody have any thoughts on this one?

Thank you..................

---

### Post by TheFu on 2016-11-28
I've been using a HandyTone 502 for over a decade with h.711u/h.729e connections. Used the HT502 with multiple SIP providers and with a commercial SIP vendor provider now (not designed for end-users). Zero support.  If you aren't fluent in SIP, then it is probably best getting something like an Ooma or paying a HW+Service provider in your area. Ooma devices come on sale all the time.

Don't know if HT still makes these things. Know that Linksys used to make "ATAs" - the devices that convert analog phones into SIP.  Cisco probably makes some now. I'm assuming you want a way to connect to normal POTS phones and not just SIP devices around the internet. A phone that can't call cell phones and businesses isn't useful to most people these days.

While I haven't checked recently, there used to be a way to use Skype for inbound and outbound calling.  I did it for about 6 months before giving up.  The voice quality sucked, the network was flakey and it was MORE expensive than the high quality provider I'm using today.  Spouse wasn't thrilled either. She's a saint for putting up with all my "projects".

Probably looking for an Ooma would be best, unless you really want to work in SIP; learn Asterisk or FreeSIP or FreeSwitch.  Telephony is like learning an entirely new language, plus if your internet isn't solid, it will suck.  Latency and tiny upstream bandwidth can make SIP terrible.  OTOH, I find it extremely frustrating to talk with people on bad POTS/Cell connections since my voice is more than CD quality these days.  BTW, the plan I'm on has free inbound calling, but pay by the minute outbound calls.

Don't really think any of this has much to do with Ubuntu, BTW.  Even when I used Asterisk on an Ubuntu server, the ATA device was still necessary for my phone system (6 handsets) to connect. Most enthusiast would dedicate something like a raspberry Pi to run Asterisk in a home and still need a $50 ATA to connect regular phone systems to that and there is still a need for an upstream SIP provider to bridge SIP into POTS.

Clear as mud?

---

### Post by jgw on 2016-12-03
Thank for the reply!  (will mark this solved)

---

