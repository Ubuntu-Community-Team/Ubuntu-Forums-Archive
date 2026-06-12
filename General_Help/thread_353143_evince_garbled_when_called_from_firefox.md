---
title: "evince garbled when called from firefox"
date: 2007-02-04
forum: General Help
---

### Post by jfenwick on 2007-02-04
When I click on a link to a pdf in firefox and it opens the file up in evince, all the menus and text of evince are garbled and replaced mostly with squares. The content of the pdf is still fine, but I can't use any of the menus since I can't read any of them.

Any ideas?

---

### Post by dcstar on 2007-02-04
> **jfenwick said:**
> When I click on a link to a pdf in firefox and it opens the file up in evince, all the menus and text of evince are garbled and replaced mostly with squares. The content of the pdf is still fine, but I can't use any of the menus since I can't read any of them.

Any ideas?

It sounds like you are missing fonts that Evince uses, I don't know what it uses but you may want to go into Synaptic and check the Dependencies in the Evince package properties.

---

### Post by jfenwick on 2007-02-04
The problem only occurs when I click on a pdf inside firefox, which launches evince. If I download the pdf file and open evince directly on the file then the menus are fine.

---

### Post by dcstar on 2007-02-04
> **jfenwick said:**
> The problem only occurs when I click on a pdf inside firefox, which launches evince. If I download the pdf file and open evince directly on the file then the menus are fine.

Maybe your Firefox is set to a different locale than your system somewhere?

You also may want to check the PDF launcher command inside Firefox to see if there are any strange parameters passed when it runs evince.

---

