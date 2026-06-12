---
title: "Different Google pages"
date: 2008-03-09
forum: General Help
---

### Post by jefft113 on 2008-03-09
I just set up firefox to use a tor proxy, when I go to google, it goes to the google page from whatever country my IP address has been routed. Once you get the main google page, you can just click on the normal google.com, but it makes the search bar useless and is a pain. Anyone know how to change the settings?

---

### Post by mreynolds on 2008-03-09
> **jefft113 said:**
> I just set up firefox to use a tor proxy, when I go to google, it goes to the google page from whatever country my IP address has been routed. Once you get the main google page, you can just click on the normal google.com, but it makes the search bar useless and is a pain. Anyone know how to change the settings?

That's juzt the nature of the beast when using tor. Google see's that your IP is from germany, it gives you the german google. I've never read about a way to always display a certain version of google. Maybe the tor site has info about how it could be done. 

I onder if you could acheve something with some /etc/hosts hackery. You could try adding entries for the different language googles to /etc/hosts to point to the .com 

Another thought, maybe you could set your google preferences to only use english google.

good luck

---

### Post by Oldsoldier2003 on 2008-03-10
> **mreynolds said:**
> 

Another thought, maybe you could set your google preferences to only use english google.

good luck

That's what i did when i lived in Germany

---

### Post by phrawzty on 2008-03-10
> **mreynolds said:**
> Another thought, maybe you could set your google preferences to only use english google.

This, in fact, is the solution.  As long as you let Google store cookies, you can store any number of preferences - including which localisation you prefer.

---

