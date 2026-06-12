---
title: "NAS device shows up twice under Networks"
date: 2021-03-14
forum: General Help
---

### Post by hatebloat on 2021-03-14
Lubuntu 12.10

I have my Seagate Personal Cloud connected to my wireless router, and it appears under Network, twice. Which one should I be connecting too?
[ATTACH=CONFIG]288129[/ATTACH]

Under Properties, the only difference in them is their name:
   dnssd-domain-PersonalCloud._afpovertcp._tcp
   dnssd-domain-PersonalCloud._smb._tcp
[ATTACH=CONFIG]288126[/ATTACH]

On the first one, double clicking it brings up the Mount prompt:
[ATTACH=CONFIG]288127[/ATTACH]

On the second NAS icon, it doesn't prompt me for info until I access a sub folder. I know from Windows that the Public folder is where my movies go in order to share. But this prompt also has a Domain field. It's just me connecting to my router, no other computers in the house, so maybe I should use the first NAS icon?
[ATTACH=CONFIG]288128[/ATTACH]

Thanks for your help, Matt

---

### Post by hatebloat on 2021-03-15
It turns out one of those icons in Network was for Apple Filing Protocol (AFP) running on my Seagate NAS. I don't need it so I disabled it in the Seagate utility webpage. Now I have just one file sharing icon in the Network window, for the SMB service running on my Seagate. The guys at Linuxquestions.org helped me with that one.

---

### Post by guiverc on 2021-03-15
Lubuntu 12.10?

That release (from 2012-October thus 12.10) reached EOL back in [mid-2014]("https://fridge.ubuntu.com/2014/05/01/ubuntu-12-10-quantal-quetzal-reaches-end-of-life-on-may-16-2014/"), so if that's your release I hope you're offline & not connected to the internet.

It could also be a typo (*looking at the pictures you provided which I'd guess are LXQt & thus more modern*), but I'd still suggest you verify your system is supported & getting security updates (unless your box is off-line and not connected to the internet).

---

