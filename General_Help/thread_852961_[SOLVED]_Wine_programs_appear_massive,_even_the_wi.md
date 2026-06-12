---
title: "[SOLVED] Wine programs appear massive, even the wine settings are huge"
date: 2008-07-08
forum: General Help
---

### Post by TroyDowling on 2008-07-08
Hey guys,

At some point, I must have changed a setting I shouldn't have or something with wine and now it's borked. Anything that I run via wine appears absolutely massive (screenshots attached). This also includes the wine settings manager itself. Since that last one is so large, I cannot edit the settings or even see what's gone bonkers. I've also tried uninstalling, uninstalling with purge and "Complete Removal" via Synaptic to no avail. I'm  a little stumped as what to do.

Wine is wine-0.9.59

Thanks for the help.

---

### Post by stinger30au on 2008-07-08
i would delete the wine directory entirely and install a fresh.

theres a few ways to do this, but if you fireup shell

and type in

gksu nautilus

go to the home directory and tell it to view all hidden files.
delete the .wine directory and reinstall

---

### Post by TroyDowling on 2008-07-08
Yes, I did try that at one point. I just realized that I hadn't removed the .wine folder from /root. That was a dumb mistake. I'll try that right now. Does anyone know if the 1.1.0 dev release is any good? I might justc ompile and run that to see how it works... Then again, I'll do all this in the morning. It's very early where I am so it's time to catch some Z's. I'll post my results here in the morning. Thanks for the quick reply.

---

### Post by Vivaldi Gloria on 2008-07-08
> **TroyDowling said:**
> Yes, I did try that at one point. I just realized that I hadn't removed the .wine folder from /root. That was a dumb mistake. I'll try that right now. Does anyone know if the 1.1.0 dev release is any good? I might justc ompile and run that to see how it works... Then again, I'll do all this in the morning. It's very early where I am so it's time to catch some Z's. I'll post my results here in the morning. Thanks for the quick reply.

I also borked my wine. Then I installed 1.1.0 using the deb file. I'm quite happy with it now.

---

### Post by TroyDowling on 2008-07-08
Well, after 'slocate'ing everything having to do with wine and removing it, I installed 1.1.0 from source. Haha, I'd like to know where you got the .deb file seeing as they're not built yet according to the WineHQ site. =) In any regard, wine now works with the small exception that it's not utilizing the Wine category of like Applications menu correctly. That's not a big deal for me seeing as I hardly used it anyways. The glitches are mostly aesthetic as well so it's no skin off my nose.

---

### Post by Vivaldi Gloria on 2008-07-08
> **TroyDowling said:**
> Haha, I'd like to know where you got the .deb file seeing as they're not built yet according to the WineHQ site. =) 

Their repos have it:

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by TroyDowling on 2008-07-09
Oh, I see that. They should definitely update the front page then seeing as it says there are no binary packages. Thanks for the tip. Well, I'm off to wine up Diablo 2 in preparation for the sequel coming out. Ha, I've been out of video games for years, but seeing that old gem resurface (as well as StarCraft 2 which I'm pumped for) brought back the memories of sitting in my basement memorizing rune combos and spell attacks. Haha.

---

### Post by TroyDowling on 2008-07-14
Just thought I'd give one last follow up for any readers coming late. I found out that the problem was that I cranked the "Screen Resolution" slider up to the max under the Graphics tag of 'winecfg'. This made all the text look huge. This setting is probably in a config somewhere; if anyone knows please tell. I only got around my problem by wiping wine and reinstalling. Not a big deal seeing as I had nothing important installed, but I'm sure other users out there will disagree.

---

