---
title: "How to turn off icon select &quot;explode&quot; animation?"
date: 2008-06-14
forum: General Help
---

### Post by Afkpuz on 2008-06-14
I'm looking to turn off the compiz animation that happens whenever I click an icon in my task bar.  You know, it the icon gets bigger and transparent.  How can I turn that off?  I can't find the plugin in compiz-settings-config.

thanks

---

### Post by Forlong on 2008-06-14
That has nothing to do with Compiz.
That is a feature of the GNOME panel itself.

Here's how to get rid of the effect:
```
gconftool-2 -s -t bool /apps/panel/global/enable_animations false
```

---

### Post by Afkpuz on 2008-06-14
thanks alot!

---

