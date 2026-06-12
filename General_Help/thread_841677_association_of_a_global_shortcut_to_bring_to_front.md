---
title: "association of a global shortcut to bring to front one application"
date: 2008-06-26
forum: General Help
---

### Post by urlwolf on 2008-06-26
I'm an autohotkey junkie.
Most the apps I use in windows have a key association.

Is it possible in linux to create an association ( global shortcut) to bring to front one application?

Thanks

---

### Post by sdennie on 2008-06-26
If you are using compiz (Desktop Effects), yes.  First:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

Then, as a test, try this from a terminal:

```

wmctrl -a "Title of a Window"

```

If that works then go to System->Preferences->Advanced Desktop Effects->General Options->Commands.  Add the commands you want to the "> Commands" section and bind them to keys in the "> Key Bindings" section.

---

### Post by urlwolf on 2008-06-27
> **vor said:**
> If you are using compiz (Desktop Effects), yes.  First:

```

sudo apt-get install compizconfig-settings-manager wmctrl

```

Then, as a test, try this from a terminal:

```

wmctrl -a "Title of a Window"

```

If that works then go to System->Preferences->Advanced Desktop Effects->General Options->Commands.  Add the commands you want to the "> Commands" section and bind them to keys in the "> Key Bindings" section.

This is great! thanks a lot!
Now I only need to find a way to dump all my onenote files into an non-proprietary format, and I'm ready to abandon windows!

Great news (for me!). I never thought it was this easy.

---

### Post by sdennie on 2008-06-27
Glad it works for you.  You may want to have a look at the man page for wmctrl because you can do just about anything to windows with that utility:

```

man wmctrl

```

---

### Post by slmingol on 2008-09-24
You can achieve the same effect without compiz. 

Using the gconf-editor you can create any keybinding you like and use wmctrl to force a window to autofocus/autoraise. The details for creating the keybinding in the gconf-editor are available here: [http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME]("http://www.linuxformat.co.uk/wiki/index.php/Setting_Key_Bindings_in_GNOME"). You can put the action using the same wmctrl -a ... command above.

---

