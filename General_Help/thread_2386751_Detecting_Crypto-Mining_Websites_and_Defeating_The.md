---
title: "Detecting Crypto-Mining Websites and Defeating Them."
date: 2018-03-09
forum: General Help
---

### Post by galacticstone on 2018-03-09
There is a disturbing new trend going around with websites using visitors' browsers to mine cryptocurrency. This causes a spike in CPU/GPU usage which can interfere with normal operations if the targeted PC is already strained for resources.

Is there a way I can detect this in real time if it is happening? Can a program like Glances or Top reveal anything, or does the browser-based nature of the event conceal it from such monitoring programs?

I have noticed that when visiting some websites, my CPU and RAM usage increases dramatically and the cooling fans kicks on - the minute I navigate away from the site, everything returns to normal.

I know I can block active scripting in the browser, but unfortunately this makes using the rest of the internet tedious since so many sites use scripting for a variety of purposes that don't involve hijacking your PC to mine crypto-currency.

I am using the latest version of Chrome - are there any browsers that cannot be hijacked to mine cryptocurrency (without turning off all active scripting) ???

Thanks!

 MikeG

---

### Post by QIII on 2018-03-09
I would block scripting and then whitelist sites where you would like scripts to run.  

There are apparently some XSS attacks that go to Pirate Mining Bay, which is running a "trial" as a way to make revenue other than advertising.  I have to throw the feldercarb flag on the field for that.

---

### Post by galacticstone on 2018-03-09
Thanks for the quick reply. I didn't realize there was a white-listing option for blocking scripting - I just thought it was a yes/no or on/off type of binary affair. This is good to know. I guess I need to explore my advanced settings in my browser a little more.  :)

On a related note - with more and more web activity taking place within the confines of the web browser, it would be interesting to see a Top or Glances type of program/extension that would show in real time everything the browser is doing on the behalf of the websites it visits. Or maybe there already is and I just not aware of it (like whitelisting scripting for websites).

> [COLOR=#000000]There are apparently some XSS attacks that go to Pirate Mining Bay, which is running a "trial" as a way to make revenue other than advertising. I have to throw the feldercarb flag on the field for that.[/COLOR]

A recent blog entry on Distrowatch discussed this and they are thinking about implementing it there - that would be a shame because I would hope they would not resort to such tactics. I would much rather pay a small fee to access the site's info or get rid of ads, than have my browser/PC hijacked.

I guess this is the downside of widespread Ad-Blocker usage....

---

### Post by kerry_s on 2018-03-09
well if use chrome right click the top-> task manager

i don't use adblock anymore either, it's a cat & mouse game, the lists get bigger, loading times get longer.
i prefer the script blocker as well, it lets me chose what to block on sites i actually visit.
[ATTACH=CONFIG]278883[/ATTACH]

---

### Post by dragonfly41 on 2018-03-10
I have read that there is interest in adding crypto mining as a new category in OpenDNS.

[URL="https://support.opendns.com/hc/en-us/community/posts/115020085963-Blocking-Cryptocurency-mining-sites"]https://support.opendns.com/hc/en-us/community/posts/115020085963-Blocking-Cryptocurency-mining-sites
[/URL]

---

