---
title: "I need to downgrade my version of Wine..."
date: 2007-10-09
forum: General Help
---

### Post by mjpatey on 2007-10-09
I've been running the only "essential" Windows program that I still need under Wine.  It's specialty software used at my church and I need the actual program here at home.

Well, the software ran PERFECTLY under Wine 0.9.45... but with the recent update, which I downloaded ](*,) , there are some serious regressions and my software won't even run.  The installer runs, but the installed app is dead in the water.

In Synaptic, I was able to downgrade to Wine 0.9.33, but that's no better... exactly the same result.

Does anybody know where I can find an Ubuntu copy of Wine 0.9.45?  I searched the Wine site, and the best they offer is a version from last year, which is even older than 0.9.33.

Thanks for any help you can provide!

-Mark

---

### Post by mjpatey on 2007-10-09
Just had an epiphany of search engine insight and found this...

[http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

That appears to be what I need!  Thanks just the same for reading. :-)

-Mark

---

### Post by pizpot on 2008-02-08
I ran into this last night.

To downgrade wine, uninstall it:

sudo apt-get remove wine

Then get wine 9.45 for ubuntu 7.04 (even though you are at 7.10 don't fret) from here:

i386:
[http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb](http://wine.budgetdedicated.com/archive/ubuntu/feisty/wine-dev_0.9.45~winehq0~ubuntu~7.04-1_i386.deb)

Then run that, then go into Synaptic and lock the version so it does not upgrade by clicking System->Administration->Synaptic Package Mager and searching for wine, selecting "wine" in the list, and clicking Package->Lock Version

Tada, now you can join Battlenet and play warcraft3 or the war3 demo till you are blue in the face. :-)

---

