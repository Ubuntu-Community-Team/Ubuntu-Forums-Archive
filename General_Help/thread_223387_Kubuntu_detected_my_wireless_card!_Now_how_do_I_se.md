---
title: "Kubuntu detected my wireless card! Now how do I set it up?"
date: 2006-07-26
forum: General Help
---

### Post by Over Haze on 2006-07-26
Pretty much as the title says for Kubuntu (unlike Ubuntu) detected my usb wireless and installed the drivers for it. I entered my wep key and the wireless connection was definitely active but I still could not connect to the internet via my network. So what am I doing wrong. Do I have to enter further details beyond my wep keys?

---

### Post by ThrobbingBrain66 on 2006-07-26
did you correctly identify the WEP as hexidecimal or ascii? that was my problem when I had trouble connecting to my network.

---

### Post by mattyh on 2006-07-26
I noticed that when getting my realtek 8150 onboard wireless to work I had to go into Networking (I think under System->Preferences but I'm at work so I'm not 100% on that) and put the settings in there initially before I was able to get an address through DHCP.  Running dhclient wlan0 wasn't sufficient.  I'm using Network Manager, which is great.

---

### Post by Over Haze on 2006-07-26
I'm pretty sure I WEP was identified. Do I have to say enter my network name or password?

---

### Post by jimbren on 2006-07-26
can you connect if you disable WEP on the router and in your setup?

---

### Post by Over Haze on 2006-07-26
I haven't tried that. I'm a very populated area so I'm not sure how safe it would be.

---

### Post by jimbren on 2006-07-27
I'm just talking about trying it for troublehsooting purposes.  If you can connect with everything in the clear, you've narrowed down the problem to encryption set up.

If you open everything up and still can't connect, you won't beat your head against the wall for hours thinking it's an encryption issue when it really isn't.

make sense?

---

### Post by briarrabbit on 2006-08-02
Don't forget to make sure your key entries match in both Network Settings & Wireless Assistant (if you use that)....screwed me up a couple of times.  I had a similar problem with Ubuntu v. Kubuntu. Both saw my card, but Ubuntu would just lock up when I tried connecting...

---

