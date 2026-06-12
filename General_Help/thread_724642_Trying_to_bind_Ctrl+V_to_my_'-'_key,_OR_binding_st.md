---
title: "Trying to bind Ctrl+V to my '-' key, OR binding strings to keys"
date: 2008-03-14
forum: General Help
---

### Post by ExtremeClean on 2008-03-14
Hey hey 

i am looking for a way to bind a string to a particular key 

such as "9999" to the minus key

i want this to be global setting.

alternatively

I would also like to be able to bind the CTRL + V to a single key on my numpad, However this is being quite difficult, Ive tried xmodmap, keymaps, etc.

if anyone knows how to solve either of these , it would be greatly appreciated

---

### Post by pointone on 2008-03-15
You should be able to use "acpi_fakekey". Check /usr/share/acpi-support/key-constants for key codes. For example, in key-constants, I see "KEY_T=20".

```
sudo acpi_fakekey 20
```

... writes the letter t in the terminal.

---

### Post by ExtremeClean on 2008-03-17
ya i looked through all that but could not find any guide on how to bind those acpi values to actual keys :(

---

### Post by pointone on 2008-03-17
You can set [custom global kebindings]("http://blog.ubrio.us/gnome/custom-global-keybindings-in-gnome-ubuntu/") with gconf-editor that run acpi_fakekey commands.

---

### Post by realn on 2008-03-27
Or you can try this one
[http://matias.ca/optimizer/index.php](http://matias.ca/optimizer/index.php)

---

