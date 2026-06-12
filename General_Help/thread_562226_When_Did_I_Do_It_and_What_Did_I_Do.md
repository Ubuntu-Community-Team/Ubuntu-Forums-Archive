---
title: "When Did I Do It and What Did I Do?"
date: 2007-09-28
forum: General Help
---

### Post by Jose Catre-Vandis on 2007-09-28
Can Ubuntu/Linux tell me when I first installed it, what I have installed to it since I started, what it has installed, how well it is working etc?

---

### Post by rsambuca on 2007-09-28
If you open Synaptic Package Manager, you can go to "File -> History" and it should give you everything you installed by date.  If you installed something manually though, I don't think it will be included here.

The rest of the stuff?  Not sure!

---

### Post by forestpixie on 2007-09-28
this will give you a list of everything installed 

```
dpkg -l | grep '^ii' | awk '{print $2}' > packages-list.txt
```

Edit - thanks to whoever's post I found it on originally :)

---

### Post by Jose Catre-Vandis on 2007-09-28
> **rsambuca said:**
> If you open Synaptic Package Manager, you can go to "File -> History" and it should give you everything you installed by date.  If you installed something manually though, I don't think it will be included here.

The rest of the stuff?  Not sure!


Thanks rsambuca. So is it safe to assume that the first entry is the date of installation, or as near as I can get to it, given that synaptic will (well, always has for me) offer updates more or less immediately after installation?

---

### Post by Jose Catre-Vandis on 2007-09-28
> **forestpixie said:**
> this will give you a list of everything installed 

```
dpkg -l | grep '^ii' | awk '{print $2}' > packages-list.txt
```

Edit - thanks to whoever's post I found it on originally :)

Hey forestpixie, sure tells me what is there. I also have found and used, simply:
```
dpkg -l
``` which at least gives a bit of info about each package :)

---

