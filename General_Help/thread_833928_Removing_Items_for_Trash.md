---
title: "Removing Items for Trash"
date: 2008-06-19
forum: General Help
---

### Post by abbasali31 on 2008-06-19
I deleted my Desktop icon, and now it is in Trash which is fine, but I can empty the Desktop icon from Trash.  The message appears "Couldn't remove the desktop folder.  Folder is not empty"  I don't think that I could delete the contents in Desktop Folder while it is in Trash.

Any suggestions.

---

### Post by iaculallad on 2008-06-19
Open your terminal and input the following commands to clean your Trash:

```
sudo rm -rf /home/your_user_name_here/.local/share/Trash/*
```

or

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by oktapod on 2008-06-20
Thenk you very much. It worked form me.

---

