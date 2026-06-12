---
title: "X broke after latest updates"
date: 2018-08-23
forum: General Help
---

### Post by jjramsey on 2018-08-23
X was working this morning, but after installing updates, it mysteriously stopped working. Now I only get a text- based login, and if I try to run startx at the prompt, X dies.

I have an ATI GPU, and judging from the output of dmesg, I'm using the Radeon driver. For now, I don't know more than that. Version of Ubuntu is 18.04.1.

Any idea what updates could have caused X to break?

ETA: Finally fixed the problem. For some reason, the gdm3 package was no longer installed, and installing it brought things back to normal. I don't recall uninstalling gdm3 myself, so I don't know what happened there. Bizarre.

---

