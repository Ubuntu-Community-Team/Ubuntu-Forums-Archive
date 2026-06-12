---
title: "Emerald not working correctly (if at all)"
date: 2008-06-16
forum: General Help
---

### Post by Linux_noob616 on 2008-06-16
I tried using an emerald theme. And i've read "use alt + f12" but i don't know what they mean by that. I go into the terminal and type "emerald --replace" but as soon as i close the terminal i have no window manager.

Yes i have compiz-fusion installed. And it does work. (can use the cube. wobble windows blur them ect.)

Can anyone help me?

Also a theme i wanted to use needs the "Aurora engine" how to i get and install that?

---

### Post by techstop on 2008-06-16
The quick fix;

Press Alt + F2 and type;

```
emerald --replace
```

The theme will continue to be applied without keeping a terminal open (but only for the current session).

The long-term fix (that will last between sessions / reboots);

Install ccsm;

```
sudo apt-get install compizconfig-settings-manager
```

Open it with System>Preferences>Advanced Desktop Effects Settings. Go to the Window Decoration plugin and enter;

```
emerald --replace
```

in the command text box.

See link in my sig for more compiz, emerald and mouse pointer tips.

---

### Post by chunchengch on 2008-06-16
> **Linux_noob616 said:**
> I tried using an emerald theme...

Double click the emerald theme you download, then the Emerald Theme Manager will be opened, click **Import** to install the theme.

> **Linux_noob616 said:**
> ...Also a theme i wanted to use needs the "Aurora engine" how to i get and install that?

Here is the "Aurora engine" deb file [ATTACH]74221[/ATTACH], just double click it to install.

---

