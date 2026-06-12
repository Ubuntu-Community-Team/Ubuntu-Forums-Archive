---
title: "[SOLVED] Ad-Blocking Filters on Epiphany?"
date: 2008-05-09
forum: General Help
---

### Post by ivansf92 on 2008-05-09
Is there any way to get the AdBlock subscriptions EasyList, EasyElement, and the Tracking Filter that were meant for the AdBlock Plus firefox extension onto Epiphany? (This is the one thing that's preventing me from premanently switching over to Epiphany.)

---

### Post by sdennie on 2008-05-09
I'm not familiar with those filters but, the epiphany adblock updates from Filterset.G so, I would imagine the file formats are compatible.  Epiphany stores it's white/blacklist files in ~/.gnome2/epiphany/extensions/data/adblock so, if you just grab the filters you want (probably just steal them directly out of your firefox directory) and concatenate them into the blacklist, it should do what you want.

---

### Post by ivansf92 on 2008-05-09
On my computer, there wasn't a ~/.gnome2/epiphany/extensions/data/adblock directory. It only went up to .gnome2/epiphany and then the only folders were favicon_cache and mozilla. Also, if the adblock plus filter was .mozilla/firefox/6fui1txl.default/adblockplus/patterns.ini, I couldn't find any .ini files in .gnome2/epiphany.

---

### Post by ivansf92 on 2008-05-09
I was reading about Epiphany a bit and it said on a website that the adblock extension had to be enabled? Does anyone know how to enable it if it does need to be enabled? (Or did I just not install the package for it, because I just entered the command sudo apt-get install epiphany-browser in the terminal.)

---

### Post by sdennie on 2008-05-09
Have you installed the epiphany-extensions package and enabled Adblock in epiphany?  I just tried on a clean Hardy install and that is the correct directory.

---

### Post by ivansf92 on 2008-05-09
> **vor said:**
> Have you installed the epiphany-extensions package and enabled Adblock in epiphany?  I just tried on a clean Hardy install and that is the correct directory.

Sorry, stupid mistake... I didn't install the epiphany-extensions package. I enabled the Adblock extension and everything is okay. Thanks.

---

### Post by DJ_Peng on 2009-08-02
> **sdennie said:**
> I'm not familiar with those filters but, the epiphany adblock updates from Filterset.G so, I would imagine the file formats are compatible.  Epiphany stores it's white/blacklist files in ~/.gnome2/epiphany/extensions/data/adblock so, if you just grab the filters you want (probably just steal them directly out of your firefox directory) and concatenate them into the blacklist, it should do what you want.

I realize this thread is marked [SOLVED] but I wanted to share what I found to work in case anyone else comes upon this thread and was as confused as I was. I tried going to the [Adblock Plus subscription page]("http://adblockplus.org/en/subscriptions") and saving the list for EasyList into my /home/peng2/.gnome2/epiphany/extensions/data/adblock but it didn't get picked up, so what I did was to open /home/peng2/.gnome2/epiphany/extensions/data/adblock/adblock-patterns in a text editor, using the link for [the EasyList list itself]("http://easylist.adblockplus.org/easylist.txt"), then copying everything below the divider line > !-------------------------Ad blocking rules--------------------------! and replacing the current contents of adblock-patterns with that. Once I saved it I opened Tools > Adblock Editor and found that my new list was there.  I know I could have kept the current contents of adblock-patterns but from my days as a Firefox user I remember posting to the [Adblock Plus Forum]("http://adblockplus.org/forum/viewtopic.php?t=2708") about a startup lag issue I had with FiltersetG and found that it didn't play all that well with ABP, and that EasyList (and the EasyList element hiding, which has now been merged into the list itself) was recommended so I made the switch just to see if it works better for me. My main goal for now is to get to where I can stop having to disable Adblock when I'm trying to watch a video on MLB.com.  Although a better solution would be to move to using Adblock Plus rather than the original Adblock. Among the Firefox community it's been an known issue for well over a year that [development on Adblock has been **ended for about five years**]("http://adblockplus.org/en/faq_project#adblock") so it makes me scratch my head and wonder why Epiphany hasn't made the switch yet. That is unless the GNOME devs have merged the changes made in AdblockPlus into their Adblock extension, but that makes me wonder why haven't named their addon &quot;Adblock Plus&quot;, especially since any Firefox user moving to Epiphany probably know that Adblock Plus is the preferred addon. But that may just be me.

---

