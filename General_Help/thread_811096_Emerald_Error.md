---
title: "Emerald Error"
date: 2008-05-28
forum: General Help
---

### Post by sifon187 on 2008-05-28
I have install Emerald and ran the cmd emerald --replace. Emerald controls the themes to a point

I get this error when I run the cmd emerald --replace

[PHP]sifon187@sifon187-laptop:~$ emerald --replace
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: Invalid symbolic color 'tooltip_bg_color'
/usr/share/themes/Darklooks/gtk-2.0/gtkrc:181: error: invalid identifier `tooltip_bg_color', expected valid identifier

[/PHP]

When I change the Emerald them, it only changes the title bars of windows and not the inside walls of the windows. Also, the task bars do not change with different themes, just stays the default Ubuntu color. Any ideas?

---

### Post by Genius314 on 2008-05-28
The error is with your GTK theme.
```
sudo gedit /usr/share/themes/Darklooks/gtk-2.0/gtkrc
```
Go to line 181, and it should have "tooltip_bg_color" in it. Comment out the line by adding a # in front of it. Save the file, and log out and back in. You shouldn't see the error anymore (hopefully).

Also, emerald controls just the title bars and window borders. Everything else is done by GTK. Fixing that line might fix the "default Ubuntu color" problem. Sometimes if the theme has an error like that, it won't load at all.

---

### Post by sifon187 on 2008-05-29
Thnx, I will try that out when I get home from work.

---

