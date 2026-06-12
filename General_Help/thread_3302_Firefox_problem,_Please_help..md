---
title: "Firefox problem, Please help."
date: 2004-11-04
forum: General Help
---

### Post by akamjballar on 2004-11-04
I was trying to upgrade my current version of firefox. So I just uninstalled the version I had, then I went via sudo apt-get install firefox. It gave me an error, so I tried doing it via synaptic. It told me to insert the ubuntu cd rom. But the problem is that, I don't have the cd anymore. I let my friends borrow it and install it. Please tell me how I can reinstall it.

---

### Post by adbak on 2004-11-04
Dunno if this will work, but edit your /etc/apt/sources.list so that it doesn't read from the CD repository, click refresh, and search from there.

---

### Post by Burgundavia on 2004-11-04
To do this is Synaptic, go to Settings --> Repository. Uncheck the line labelled cdrom, which is usually the 1st line. This will automattically update your sources.list

Corey

---

### Post by akamjballar on 2004-11-05
Thank you very much. That worked fine.

---

