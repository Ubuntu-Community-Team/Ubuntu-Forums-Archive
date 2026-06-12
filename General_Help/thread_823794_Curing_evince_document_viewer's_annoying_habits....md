---
title: "Curing evince document viewer's annoying habits..."
date: 2008-06-09
forum: General Help
---

### Post by ticopelp on 2008-06-09
...is there any way to?

Document Viewer is a great way to look at PDFs -- it's faster and smoother than using Adobe Reader, but every time I open a PDF it's 1) magnified and 2) the document window is so big that I have to drag it over and resize it to get it to fit on the screen. This gets so annoying after the millionth time.

Is there a setting somewhere I can change to make evince open PDFs at a reasonable magnification and window size?

---

### Post by kaibob on 2008-06-10
> **ticopelp said:**
> ...Is there a setting somewhere I can change to make evince open PDFs at a reasonable magnification and window size?

Normally, Evince remembers the last view setting and utilizes that setting when it next loads. For example, I normally have *view > page-width* checked, and it's checked the next time I load Evince.

There is a key in the configuration editor that overrides document settings. It's checked by default, but you may want to make sure this key hasn't been changed. The key is:

/apps/evince/override_restrictions

Otherwise, I don't know what's going on.

---

