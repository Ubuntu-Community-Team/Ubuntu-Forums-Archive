---
title: "privacy in prism apps for gmail, facebook, etc."
date: 2008-07-08
forum: General Help
---

### Post by waster on 2008-07-08
I am starting to use the prism application to have things like gmail and facebook independent of my main browsing. My goal is to keep the scattering of cookies and click tracking away from firefox. However, I don't know whether prism applications, together or individually, keep cookies, passwords, cache etc separate.

It would also be useful to add firefox extensions, especially ad-block plus, but this doesn't seem possible right now.

So how much data do prism applications share with each other, and with firefox?

---

### Post by hyper_ch on 2008-07-08
what are prism applications?

If you're worried, use different browsers... like FF for normal surfing and Opera for all GMail, ...

---

### Post by lut4rp on 2008-07-08
- AFAIK all Prism apps keep data together, since they are just instances of xulrunner.
- They share the same Firefox core, but they don't share any data with FF.

---

### Post by Vivaldi Gloria on 2008-07-08
I have prism 0.8 and it keeps its cache in

```
~/.prism/<defaultuser>/cache
```

All webapps share it. I don't know what prism 0.9 does.

---

### Post by waster on 2008-07-12
> **lut4rp said:**
> - AFAIK all Prism apps keep data together, since they are just instances of xulrunner.
- They share the same Firefox core, but they don't share any data with FF.

Thanks - that what I wanted to confirm.

---

