---
title: "ekiga add codecs"
date: 2006-11-18
forum: General Help
---

### Post by aliyanage on 2006-11-18
Hi all,

I've opened up an account on [www.voipcheap.com](www.voipcheap.com) and now I would like to use it with ekiga using the sip details. I've basically set everything up and I was able to ring out but the sound is flakey and broken up. Cant really make any phone calls like that. I don't know exactly what the reason is but I assume I need to use the G.711 codecs which is not available in ekiga, my question is whether it is possible to add the G.711 codecs to ekiga?

would be really great if someone could give me some help on this one, thanks.

aliyanage :-k

---

### Post by aliyanage on 2006-11-21
Hi all,

I found out it didn't have anything to do with the codecs. All I had to do is set the Audio deviced to default.

so go to:
-ekiga preferences
-devices
-audio devices
and then set the output device as well as the input device to default

I just wanna write down all my settings in case someone would like to set up a sip using an account from voipcheap.com. (Ekiga Softphone 2.0.3)

1. Go to voipcheap.com register and make urself an account

2. Go to Applications/Internet/Ekiga Softphone (installed by default in Ubuntu)

3. Cancel the **configuration druid** and go to **Edit/Accounts** and click **Add**.

4. **Account name:** VoipCheap (free to choose)
**Protocol:** SIP
**Registrar:** sip.voipcheap.com
**Username:** (username from voipcheap)
**Password:** (password from voipcheap)
**Authentication Login:** (username from voipcheap)
**Realm/Domain:** voipcheap.com
**Registration Timeout:** 3600

And then close accounts window.

5. Go to **Edit/Preferences**
-Go to **General/SoundEvents** and set alternative output device to default.
-Go to **Protocols/NetworkSettings**
NAT Traversal Method: STUN
Stun Server: stun.voipcheap.com
and then click on Apply.
-Go to **Protocols/SIPSettings**
Outbound Proxy: sip.voipcheap.com
-Go to **Devices/AudioDevices**
Audio Devices Output Device: default
Audio Devices Input Device: default

And that's it, worked fine with me and I am doing my free landline calls to most of the countries I like to phone :-D

---

