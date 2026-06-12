---
title: "Ubuntu 18.04+KDE add printer GTK-critical"
date: 2018-09-20
forum: General Help
---

### Post by mishgenn on 2018-09-20
Open terminal, then
> sudo system-config-printer

then in printers window do Add, in terminal I have:

> (system-config-printer:3161): Gtk-CRITICAL **: 16:41:19.094: gtk_tree_store_insert_after: assertion 'G_NODE (sibling->user_data)->parent == G_NODE (parent->user_data)' failed

(system-config-printer:3161): Gtk-CRITICAL **: 16:41:19.094: gtk_tree_store_set_value: assertion 'VALID_ITER (iter, tree_store)' failed

(system-config-printer:3161): Gtk-CRITICAL **: 16:41:19.094: gtk_tree_store_set_value: assertion 'VALID_ITER (iter, tree_store)' failed



How to fix?

---

### Post by Autodave on 2018-09-20
Exactly what are you trying to do: install a printer?  If so, what make and model?  How is it connected to the PC?

---

### Post by mishgenn on 2018-09-21
I see an error in the terminal after pressing the add button, even before selecting the printer type and its model. All printers connected to PC's with Windows.

---

