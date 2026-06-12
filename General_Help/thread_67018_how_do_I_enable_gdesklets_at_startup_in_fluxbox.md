---
title: "how do I enable gdesklets at startup in fluxbox?"
date: 2005-09-19
forum: General Help
---

### Post by Ibuntu_52 on 2005-09-19
Does anyone know how to make gdesklets start at startup in fluxbox?

I followed this guide: [http://gentoo-wiki.com/HOWTO_Autostart_Programs](http://gentoo-wiki.com/HOWTO_Autostart_Programs)

but I couldn't get it to work

If I get this working I'll turn this how-do into a how-to ;-)

---

### Post by Xian on 2005-09-19
Well, it's right in the link you provided so I'm not sure what the issue is on your system. I just added the following line to my ~/.fluxbox/startup file:

```
gdesklets start &
```

---

