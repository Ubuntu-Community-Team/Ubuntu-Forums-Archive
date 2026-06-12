---
title: "gnome-panel key screwed up. error..."
date: 2006-07-13
forum: General Help
---

### Post by disturbd on 2006-07-13
Couple days ago i was trying to get the desktop icons to show up. I got them but i also screwed up one of the keys. Now everytime i login i get this error in a popup window:

"An error occured while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly"

DETAILS
"Type mismatch: Expected "'string' got 'int' for key /apps/nautilus/desktop/computer_icon_name"

Everytime i try to delete the key it comes back but its not the right one. It's the one i messed up.

Is there anyway to restore the key to its original?

Thanks

---

### Post by ayoli on 2006-07-13
run gconf-editor and change value of this key:
```
/apps/nautilus/desktop/computer_icon_name
```
to any string you want (ie: your hostname).
regards.

---

### Post by disturbd on 2006-07-13
i can't it says its read only. "This key is not writable"

i don't know why its like this. Even in root i cant change it.

---

### Post by disturbd on 2006-07-13
don't know if it will help but i accidentally deleted the original key. the one that its showing now is the one i tried to make to replace it. but instead of it having a checkbox like the old one it has a 1 ina box beside it. i didnt know how to make it right. shouldnt of been messing with it in the first place i guess.

---

### Post by ayoli on 2006-07-13
when you double clic the key in gconf-editor you normally can change the type (int/boolean/string) this key is supposed to be a string
but if it still don't work you can try to re-install nautilus to have deeult keys restored.
regards.

---

### Post by disturbd on 2006-07-13
thanks. thats what i figured i'd have todo. is there anyway i can reinstall it from the live cd because i dont have it on the internet right now?

---

### Post by disturbd on 2006-07-13
anyone? i need to reinstall nautilus from the live cd. i downloaded the deb and tried it that way but i get errors.

---

### Post by ayoli on 2006-07-14
> **disturbd said:**
> anyone? i need to reinstall nautilus from the live cd. i downloaded the deb and tried it that way but i get errors.
what errors ? if you already made upgrades of your dapper and if you try to reinstall from cd an older version that could be the pb.
regards.

---

### Post by mcduck on 2006-07-14
You could just remove the panel that's causing you problems, and then make a new one & add all applets you need to that new panel :)

---

### Post by testube_babies on 2006-07-14
> **mcduck said:**
> You could just remove the panel that's causing you problems, and then make a new one & add all applets you need to that new panel :)

I'd recommend this.  If you are still having troubles, you can reset all of the keys in that particular folder:
```

gconftool-2 --recursive-unset /apps/nautilus/desktop
```

If that fails, you can reset the entire nautilus folder:
```

gconftool-2 --recursive-unset /apps/nautilus
```

---

