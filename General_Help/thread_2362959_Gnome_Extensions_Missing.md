---
title: "Gnome Extensions Missing"
date: 2017-06-04
forum: General Help
---

### Post by gr8 on 2017-06-04
I have a ton of GNOME extensions running, enabled and working properly. How come only half of them show up in my _*/usr/share/gnome-shell/extensions/*_ folder? For instance Dash-to-Dock is running right now but it doesn't show up there as it's own folder. It used to, yet it still works properly!

---

### Post by tea for one on 2017-06-04
Good evening

Have a quick look at the hidden file in your home directory:-

.local/share/gnome-shell/extensions

---

### Post by monkeybrain20122 on 2017-06-04
They only show up in /usr/share if you installed them system wide (that means via sudo apt-get or synaptic or the software centre) If you installed them from the website you only installed them in your $HOME. In that case they are in .local/share as tea for one said. To view .local open the file manager and press ctrl+h or choose "show hidden" in menu to show hidden directories.

---

