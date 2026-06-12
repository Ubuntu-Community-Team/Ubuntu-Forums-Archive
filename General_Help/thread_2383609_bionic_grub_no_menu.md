---
title: "bionic: grub no menu"
date: 2018-01-27
forum: General Help
---

### Post by MyMurry on 2018-01-27
Hello,

I can't get a grub menu on my system:

I tried this entries:

/etc/default/grub

```

**#**GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true


```

I also removed the entry, reinstalled grub, changed the boot partition.

Nothing help.

Is this a know problem? Any hints?:(

Regards,

Norbert

---

### Post by coffeecat on 2018-01-27
What release number and flavour of Ubuntu are you using?

---

### Post by MyMurry on 2018-01-27
I found a wrong entry in /etc/grub/40_custom

---

### Post by coffeecat on 2018-01-27
@MyMurry, you didn't answer my question. The reason I asked it was that you posted in the Ubuntu Development Version section, which is for discussions concerning the development versions only, and my guess is that you are probably using a standard released version of Ubuntu. 

Therefore, *thread moved to **General Help**.*

Your latest post is somewhat cryptic, but you've tagged the thread solved, so can we assume that you've found the problem, or do you need any help from the forum membership?

---

