---
title: "Quick Question.... Wine and NFTS"
date: 2007-05-02
forum: General Help
---

### Post by cmmike1 on 2007-05-02
Is it possible to run programs on your windows partition through wine while using the nfts driver?

---

### Post by kalpik on 2007-05-02
Quick answer: Yes :D

---

### Post by cmmike1 on 2007-05-02
Can anyone else confirm this? Also is the nfts driver stable yet?

---

### Post by cmmike1 on 2007-05-02
anyone?

---

### Post by YokoZar on 2007-05-03
Yes, but you don't want to.  You want to install applications "fresh" into Wine's virtual windows drive.

The reason for this is that Wine won't be able to access whatever those programs put into the Windows registry when they were installed, since they won't be in Wine's registry.  Sometimes this breaks applications, unless they were specifically designed to be portable (ie, not use the registry at all)

---

### Post by orb9220 on 2007-05-03
> Is it possible to run programs on your windows partition through wine while using the nfts driver?

No anyone saying yes is giving you FUD.

Wine uses it own special fake windows directory in the .wine folder.
Apps that run need to be installed there.

And you can't just install and run any apps.

---

### Post by cmmike1 on 2007-05-03
> **orb9220 said:**
> No anyone saying yes is giving you FUD.

Wine uses it own special fake windows directory in the .wine folder.
Apps that run need to be installed there.

And you can't just install and run any apps.

alright. thank you,

---

