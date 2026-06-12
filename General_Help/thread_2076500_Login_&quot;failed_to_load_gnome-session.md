---
title: "Login &quot;failed to load gnome-session"
date: 2012-10-26
forum: General Help
---

### Post by Yumi on 2012-10-26
Managed to solve that problem by switching from default "lightgdm" to "gdm"

I did it like this:
Ctrl+Alt+F2 to get the prompt
then
sudo apt-get remove --purge gdm
sudo apt-get install gdm

the first window ok, the second window select gdm an ok. Restard.

Michael

---

