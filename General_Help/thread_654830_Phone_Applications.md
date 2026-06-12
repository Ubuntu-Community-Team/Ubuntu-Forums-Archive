---
title: "Phone Applications"
date: 2007-12-31
forum: General Help
---

### Post by sekinto on 2007-12-31
I know about VOIP and internet calls. But I'm wondering if there is a way to hook your computer up to your phone cord and make/receive calls?

---

### Post by kyphi on 2007-12-31
1.  VoIP phone calls can be made via a modem/router using your ordinary phone but you must have an ISP that will provide that service for a fee plus the cost of calls which are cheaper than landline calls.

2.  VoIP phone calls can be made via a softphone such as Ekiga (in your Ubuntu installation).  To another Ekiga user these calls are free, to make calls to those who do not use Ekiga will cost money.

3.  All phone uses are made via a router/modem.  That is the main component.

---

### Post by sekinto on 2007-12-31
What I mean is I want to make ordinary calls like I would on a normal phone, but using my laptop instead of a phone. Isn't there a way to make my laptop mimic a phone with an application and just use my normal phone service?

---

### Post by kyphi on 2007-12-31
No, this can not be done.

That is what mobile phones are for.

---

### Post by kebes on 2007-12-31
> **sekinto said:**
> What I mean is I want to make ordinary calls like I would on a normal phone, but using my laptop instead of a phone. Isn't there a way to make my laptop mimic a phone with an application and just use my normal phone service?

It depends on exactly what you mean...

It sounds like you want to plug your normal phone line (with normal telephone provider) into your computer, and then use your computer's microphone and speakers to conduct the phone call. If that's what you want, then you need a telephony access card (a normal modem can't do it, you need an FXO/FXS card like [this]("http://www.digium.com/en/products/digital/te120p.php")), and then you install some software like [Asterisk]("http://www.asterisk.org/") and use a software-phone to make/receive calls.

These computer-controlled [PBX]("http://en.wikipedia.org/wiki/Pbx") systems can be as sophisticated as you want (you can use Asterisk, for instance, to act as an answering machine, create call-menus, etc.).

Of course this is a somewhat complicated solution if all you want is a phone hooked up to a normal phone line.



If you instead want an entirely software-based telephone on your computer, then you can use something like [Skype]("http://www.skype.com/welcomeback/") or [OpenWengo]("http://www.openwengo.org/"), but then you have to pay a service fee to connect your Internet-based call to normal telephone numbers.


Hope that helps.

---

