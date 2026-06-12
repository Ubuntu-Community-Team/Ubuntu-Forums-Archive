---
title: "Ubuntu &quot;mount&quot; changes"
date: 2005-04-05
forum: General Help
---

### Post by lithium on 2005-04-05
Hi there, hope someone can help me.

I'm using ubuntu hoary on two systems: laptop (unmodified copy) and desktop where I only want to use the base system and install various software from source (gnome etc)

The only problem is that I don't want to patch apps to use pmount so I want to revert to the standart model of using fstab-sync so that I can use unmodified versions of gnome-volume-manager etc

Can someone please point me to the changes that were done in the pmount transition? Can I use ubuntu's hal package when I add fstab-sync manually or do I need to rebuild it? Any configuration changes?

Thx,

Michael

---

### Post by lithium on 2005-04-10
So I just hacked up my own HAL package(es) from upstream hal-0.4.7 and added the fstab-update script from HAL CVS. Never build my own debs before but after reading the debian manual it was piece of cake... Works really well and even sorted out the error I had previously regarding a "missing feature" in my kernel (kernel was build without PCMCIA support as this is a desktop machine)

---

### Post by gbil on 2005-04-10
[QUOTE=lithium]So I just hacked up my own HAL package(es) from upstream hal-0.4.7 and added the fstab-update script from HAL CVS. Never build my own debs before but after reading the debian manual it was piece of cake... Works really well and even sorted out the error I had previously regarding a "missing feature" in my kernel (kernel was build without PCMCIA support as this is a desktop machine)[/QUOTE]
 Nice. Can you upload the packages you made?

---

