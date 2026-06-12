---
title: "Does Epiphany require Firefox?  It's a dependency in Snyaptic"
date: 2007-07-14
forum: General Help
---

### Post by timzak on 2007-07-14
Trying to remove Firefox and install Epiphany on an old, slow computer with Xubuntu and Synaptic has them as dependencies.  Is this right?  Can I remove Firefox and install Epiphany?

---

### Post by yabbadabbadont on 2007-07-14
Stupid as it seems, it appears that the epiphany-browser package in Feisty does require firefox...  Weird.

---

### Post by aysiu on 2007-07-14
It's been this way even before Feisty.

---

### Post by timzak on 2007-07-15
Yeah, I was hoping to free some hard drive space because Epiphany runs so much better than Firefox on this old computer.  Oh well.  Thanks for the replies.

---

### Post by mcduck on 2007-07-15
Epiphany uses Mozilla's Gecko engine, which is not available as a separate package. So you need to have Firefox installed to use Epiphany. There's nothing that can be done about it until Mozilla starts distributing Gecko separately from Firefox.

---

### Post by yabbadabbadont on 2007-07-15
> **mcduck said:**
> Epiphany uses Mozilla's Gecko engine, which is not available as a separate package. So you need to have Firefox installed to use Epiphany. There's nothing that can be done about it until Mozilla starts distributing Gecko separately from Firefox.

You can get the gecko engine separately.  At least you could on Gentoo.  It is all OSS after all.  You can slice and dice Mozilla/Firefox any way you like and redistribute it as long as you don't use the official branding and also redistribute your changes.  ;)

---

### Post by newagelink on 2007-07-27
> **mcduck said:**
> Epiphany uses Mozilla's Gecko engine, which is not available as a separate package. So you need to have Firefox installed to use Epiphany. There's nothing that can be done about it until Mozilla starts distributing Gecko separately from Firefox.I thought Gecko was public domain. Is it not? I mean, I thought it was open source, or something.

---

### Post by justin whitaker on 2007-07-27
> **yabbadabbadont said:**
> You can get the gecko engine separately.  At least you could on Gentoo.  It is all OSS after all.  You can slice and dice Mozilla/Firefox any way you like and redistribute it as long as you don't use the official branding and also redistribute your changes.  ;)

Well, hell, that's just crazy talk! 

Actually, it would be a good idea to break this dependency at some point...I don't have the skill to do it though. :(:)

---

### Post by fragos on 2007-07-27
Gecko isn't public domain it's some version of GPL which means the source code is available to all on a package basis.

---

