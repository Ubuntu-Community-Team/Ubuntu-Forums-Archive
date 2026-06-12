---
title: "Nautilus list view: How do I permanently change the displayed columns?"
date: 2022-08-27
forum: General Help
---

### Post by Paddy Landau on 2022-08-27
In Ubuntu 20.04, I can open Nautilus > Preferences > List Columns, and select which columns I want shown in list view.

In Ubuntu 22.04, that option isn't available. Instead, I can right-click the column bar, and select the columns what I want. But, I have to do this separately with *every single directory* that I visit.

I can't figure out how to set my choices as the default. I searched in dconf-editor, but was unsuccessful.

How do I set the columns for Nautilus, please?

---

### Post by &amp;KyT$0P# on 2022-08-27
I couldn't find a GUI way to do this, so I did it in dconf-editor modifying [FONT=Courier New]/org/gnome/nautilus/list-view/default-visible-columns[/FONT]

---

### Post by Paddy Landau on 2022-08-27
> **halogen2 said:**
> I couldn't find a GUI way to do this, so I did it in dconf-editor modifying [FONT=Courier New]/org/gnome/nautilus/list-view/default-visible-columns[/FONT]
I had to add the key, because it doesn't exist on 22.04. I took the values from 20.04, and did this:
```
gsettings set org.gnome.nautilus.list-view default-visible-columns "['name', 'size', 'owner', 'permissions', 'date_modified_with_time', 'detailed_type']"
```
It worked, thank you.

---

### Post by &amp;KyT$0P# on 2022-08-27
> **Paddy Landau said:**
> I had to add the key, because it doesn't exist on 22.04. 

Huh?  That key exist by default for me in multiple installations of both Ubuntu 22.04 and Pop!_OS 22.04 (which is based on Ubuntu and also uses GNOME)

Sorry I don't know how to troubleshoot why it's missing for you, but good to hear this solution still worked for you.

---

### Post by Paddy Landau on 2022-08-28
> **halogen2 said:**
> Huh?  That key exist by default for me in multiple installations of both Ubuntu 22.04 and Pop!_OS 22.04
How odd! My installation must be… curious.

---

