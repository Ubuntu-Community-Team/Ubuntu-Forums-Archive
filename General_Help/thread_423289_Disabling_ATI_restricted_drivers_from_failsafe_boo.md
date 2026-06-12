---
title: "Disabling ATI restricted drivers from failsafe boot?"
date: 2007-04-25
forum: General Help
---

### Post by PhatStreet on 2007-04-25
After activating them in the manager, my system freezes after the boot progress bar goes to 100%. I can load failsafe no problem, though. How exactly can I disable these?

---

### Post by desheikh on 2007-04-25
sudo gedit /etc/X11/xorg.conf

under section device replace fglrx with ati

and your done!

---

