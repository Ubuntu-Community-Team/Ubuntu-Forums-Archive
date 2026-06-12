---
title: "gedit no menu"
date: 2020-02-25
forum: General Help
---

### Post by ffrr on 2020-02-25
The other day I upgraded from 16.04 to 18.04 and now Gedit has no menu. Previous posts indicate that this has to do with terminals. I am using Mate and Gedit worked just fine before the upgrade. 
Thanks for any help.

Frederic

---

### Post by EuclideanCoffee on 2020-02-25
What happens when you try executing /usr/bin/gedit in the terminal?

---

### Post by ffrr on 2020-02-25
No difference. A Gedit window opens and it has no menu.

---

### Post by Dennis N on 2020-02-25
By menu, do you mean 'menu bar'? Mate 16.04 applications were mostly gtk2 based and had menu bars. Newer gedit is a gtk3 application and doesn't have a menu bar anymore in accordance with modern Gnome styling. No menu bar, but it should have a menu button (and maybe an options button) next to the "Save" button.

---

