---
title: "Synaptic screen is confusing...do I have broken packages or not?"
date: 2007-10-21
forum: General Help
---

### Post by bpont on 2007-10-21
Take a look at [this screenshot]("http://img81.imageshack.us/img81/1218/screenshotkw9.png").  It apparently lists dozens of packages as broken, yet at the bottom it says no packages are broken.  I highlighted all the so-called broken packages and ran the 'fix broken packages' command, but the screen still looks the same, even after a reboot.  Am I missing something here??

---

### Post by por100pre1 on 2007-10-21
It seems Synaptic is actually missing something here.

```
sudo apt-get install -f
```

I think it is a good idea to file a bug report against Synaptic in Launchpad. :-k

---

