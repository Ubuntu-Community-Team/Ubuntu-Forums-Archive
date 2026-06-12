---
title: "emerald themes"
date: 2008-05-01
forum: General Help
---

### Post by louishr on 2008-05-01
I'm new to linux and i just installed 8.04 the other day. I want to apply an emerald theme i downloaded. I downloaded and installed emerald theme manager. i run the app and import the theme but nothing changes, how do i activate the theme?

---

### Post by yogo on 2008-05-01
You have to select the theme in Emerald, simply by clicking on it.

---

### Post by louishr on 2008-05-01
well i do but nothing happens, i can import themes, they show up in the window inside emerald, but clicking them does absolutely nothing. Any ideas as to what is wrong?

---

### Post by chad_s on 2008-05-01
[http://ubuntuforums.org/showthread.php?t=776734](http://ubuntuforums.org/showthread.php?t=776734)

---

### Post by Zorael on 2008-05-01
That means you're not running emerald.
[list][*]If you're running fusion-icon, select emerald as your window decorator.
[*]If you have the Window Decorations plugin enabled in ccsm (configconfig-settings-manager, try entering 'emerald --replace' in the command field in its settings
[*]Just try entering 'emerald --replace' in a run box (Alt+F2)[/list]

---

### Post by maddy_in65 on 2008-05-01
I have a problem with emarald themes whenever i start my PC i need to do 'emarald replace' every to get emarald work. Please tell me what can be done to avoid this every time

---

### Post by Zorael on 2008-05-01
Grab the **fusion-icon package**. It'll install an app that puts an icon in your systray, with which you can set which window decorator you want (emerald).

If Gnome: make an entry that launches '**fusion-icon**', under Sessions.
If KDE: make a symbolic link under **~/.kde/Autostart** toward **/usr/bin/fusion-icon**.
```
$ ln -s /usr/bin/fusion-icon ~/.kde/Autostart/fusion-icon
```
Like so.

---

