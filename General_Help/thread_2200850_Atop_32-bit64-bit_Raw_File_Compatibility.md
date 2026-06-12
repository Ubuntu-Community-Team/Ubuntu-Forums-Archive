---
title: "Atop 32-bit/64-bit Raw File Compatibility"
date: 2014-01-21
forum: General Help
---

### Post by Kirk Schnable on 2014-01-21
I encountered an interesting problem while gathering atop data from a batch of computers.  I came up with a way to send all the atop raw files to a central location, but now I can't actually process them, because of this daunting error:

```
# atop -r filename
raw file filename has incompatible format
(created by version 1.26 - current version 1.26)
```

What I have found is that 64-bit machines seem to be able to open atop raw files from other 64-bit machines, and 32-bit machines seem to be able to open atop from other 32-bit machines.

I would like to devise a way to somehow make my 64-bit server able to parse the files from our 32-bit machines.  Is there a way I could perhaps install a compatibility library or install the actual 32-bit version of atop on this 64-bit server, or am I going to have to end up provisioning a 32-bit VM to read these 32-bit raw files?

Thanks in advance for any suggestions!

---

