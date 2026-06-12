---
title: "Window Border Magnified (text and buttons too big)"
date: 2008-03-07
forum: General Help
---

### Post by ian320 on 2008-03-07
I am running Ubuntu 7.10 and Compiz Fusion, and I noticed that my window border (metacity) themes show up with enlarged text and buttons when I use Compiz Fusion.

I am using the Aurora theme/engine for metacity, and I noticed that the window title text was much bigger than on other Gnome computers, but it is especially apparent after running the following commands:

```
metacity --replace
```

which turns off Compiz rendering, and then

```
compiz --replace gconf
```

which turns it back on. After this sequence the title bar text is the normal size and so are the buttons. I would like it to be like this all the time, and doing the commands messes up my keyboard shortcuts as set in the System > Preferences > Keyboard Shortcuts dialog. Any ideas?

---

### Post by pointone on 2008-03-07
I experienced this bug as well. Try running "gtk-window-decorator --replace" instead of metacity; it doesn't turn off Compiz, but should still work.

I solved my problem by simply creating a script to be run at the start of each session:

```
sleep 15 # wait for Compiz to be fully started
gtk-window-decorator --replace
```

---

