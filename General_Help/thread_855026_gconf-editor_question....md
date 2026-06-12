---
title: "gconf-editor question..."
date: 2008-07-10
forum: General Help
---

### Post by boblemur on 2008-07-10
this may be a stupid question... and maybe im just missing something obvious...

but in the editor if i want to change say /apps/metacity/global_keybindings/run_command_terminal

to what some diffrent value.. how can i do this outside of the gconfig-editor because im writing a script to restore all my settings after i reformat and a few of my keyboard shortcuts and stuff like that are in gconfig-editor.. i was wondering if it had either a commandline interface or a way i could find out where that value is stored that would be good..

thanks in advance

---

### Post by Vivaldi Gloria on 2008-07-10
> **boblemur said:**
> this may be a stupid question... and maybe im just missing something obvious...

but in the editor if i want to change say /apps/metacity/global_keybindings/run_command_terminal

to what some diffrent value.. how can i do this outside of the gconfig-editor because im writing a script to restore all my settings after i reformat and a few of my keyboard shortcuts and stuff like that are in gconfig-editor.. i was wondering if it had either a commandline interface or a way i could find out where that value is stored that would be good..

thanks in advance

They are strored in .gconf folder in your home.

---

### Post by boblemur on 2008-07-10
thanks that helps, how about the schemas and system options that are in gconf? my .gconf folder only contains desktop and apps ( logical however to only have my settings there.. what about others)

---

### Post by Vivaldi Gloria on 2008-07-10
> **boblemur said:**
> thanks that helps, how about the schemas and system options that are in gconf? my .gconf folder only contains desktop and apps ( logical however to only have my settings there.. what about others)

I don't know. I guess unless you add a schema that folder doesn't show up. I have a system folder:

```
vivaldi:~/.gconf$ ls
apps  desktop  system
```

But the system folder contains very little. May be only if you change something then those item's are added.

I'm just guessing here. Why don't you read about it here:

[http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/)

and maybe google it.

---

### Post by boblemur on 2008-07-10
cool ok, ill look into that,

thank you

---

### Post by Vivaldi Gloria on 2008-07-10
> **boblemur said:**
> cool ok, ill look into that,

thank you

You're welcome.

---

