---
title: "Ubuntu Won't Recognise My Wireless Card After Software Upgrade"
date: 2006-11-02
forum: General Help
---

### Post by shafty1968 on 2006-11-02
Hi Guys,

I have an Acer Travelmate laptop with a Aetheros AR5005G Wireless card.

The card was working fine until the other day when I used software update on my Ubuntu 6.06 installation; now when I try to use Wireless Assistant to scan for networks I get an error message, something about not being able to find a wireless card.

I would be very grateful if somebody could please give me some advice.

Thanks very much in advance...

---

### Post by benmoreassynt on 2006-11-02
> **shafty1968 said:**
> I have an Acer Travelmate laptop with a Aetheros AR5005G Wireless card.

The card was working fine until the other day when I used software update on my Ubuntu 6.06 installation

Can your provide some more detail?

Did the card work perfectly first time when you first installed 6.06, or did you have to do a workaround, configuration with madwifi or anything like that?

When you say 'software update', do you mean an upgrade to 6.10, Edgy Eft, or just a regular security/software update in 6.06 LTS?

There are a few threads about the Atheros and Acer on the forums - check them out (I noticed you spelled it Aetheros, which would prevent you finding them). A few people seem to have problems, but without knowing a bit more about your setup it is difficult to give advice.

If it was working before it may just be a matter of a minor change needing to be done to a config file. Edgy uninstalled the app which makes my wifi work for some reason. A reinstall and edit of a config file solved the problem.

---

### Post by shafty1968 on 2006-11-02
Yes, the card worked absolutly fine from when I first installed 6.06 and I never had any trouble with it: it is only since I did a regular security/software update (via the icon on the Ubuntu menu bar) that my card seems to have disappeared.

I am very new to Linux and this is my first set back, and I'm a bit confused; thanks again in advance for any advice...

---

### Post by benmoreassynt on 2006-11-03
I'd recommend that you go here:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

and work through it exactly as stated. This will help you get more detail about the precise card you are using, and then identify where the problem lies. For instance, is the card being recognised and receiving power, or is the problem somewhere else. If having gone through that you are still stuck, post again here with the details you've found out.

It's a pain when you had such an easy experience at first. But keep at it. Another piece of advice - write down on a bit of paper exactly what you do, in case you ever need to do it again!

---

