---
title: "Brand new to Ubuntu"
date: 2008-06-26
forum: General Help
---

### Post by chansenola on 2008-06-26
Have dabble in Linux on and off, and AM NOT going to Vista, so I installed Ubuntu. I'm loving it, but have an issue.
When I first log on, I get Network Manager applet could not find some required resources."

And as I try to load Synaptic Package Manager, I get "An Error Occured"
------------------------
E: Type '--18:10:24--' is not known on line 1 in source list /etc/apt/sources.list.d/mediabuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
---------------------------------
I gave a look at

"gksu gedit /etc/apt/sources.list" but I guess don't really know what I'm looking at. any assistance would be greatly appreciated.

---

### Post by Taxman415a on 2008-06-26
Perhaps you added medibuntu by hand and misspelled it? It doesn't have an "a". Can you show us your sources.list file?
Or maybe show us the /etc/apt/sources.list.d/medibuntu.list file. I can't tell by the error which file the error is in.
Oh and welcome! There's no turning back ;)

---

