---
title: "Removal of firefox plug ins"
date: 2007-11-01
forum: General Help
---

### Post by ke4ram on 2007-11-01
The new 7.10 is great. Firefox is so much easier except for one itsy bitsy tweeny weenie thing.

Once you load a plugin there seems no way to remove it. 
Even deleting Firefox (COMPLETELY) does not work because when they say all configuration files are removed it's a little white lie. 
When reloaded the same configuration is set up including the same plug ins. 

I'm sure the geeks could do it in a flash but I'll just reload ubuntu. It's really a sad thing.


Oh, by the way, when loading JAVA you get choices. Choose the real thing (Java 5.0 or 6.0) because the other (first choice) doe not work,,, unless of course your a expert and know the super duper top secret removal process.

I know your on your in in Linux Land but I reasoned I could be a bit different and try to help someone not make the same insane mistake.

regards

---

### Post by taurus on 2007-11-01
You can remove ~/.mozilla/firefox if you want to start over with firefox.

Applications -> Accessories -> Terminal
```
cd ~/.mozilla
rm -rf firefox <-- Your bookmarks will be gone too.
```
And if you want to remove Sun java 5, the easiest way is to open synaptic and Search for it.  Then, mark it for delete.

---

### Post by Scratches on 2007-11-01
tools -> add ons -> extensions tab -> uninstall the addons you don't want

Tom

---

