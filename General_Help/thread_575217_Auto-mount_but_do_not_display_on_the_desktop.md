---
title: "Auto-mount but do not display on the desktop"
date: 2007-10-13
forum: General Help
---

### Post by overlord.gaurav on 2007-10-13
I have Feisty Fawn and it all works fine for me here.

I just wanted to play around a little and wanted to know: How do I keep the auto mount feature and not allow the mounted drive to be displayed on the **desktop**

---

### Post by overlord.gaurav on 2007-10-13
Ok, I found it.
For anyone else who wants to do it:

```
gconf-editor
```
apps>>desktop>> uncheck volumes_visible

Also, if you have already added Configuration Editor to your menu then you can use the short-cut.

---

