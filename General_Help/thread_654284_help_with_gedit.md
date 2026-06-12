---
title: "help with gedit"
date: 2007-12-30
forum: General Help
---

### Post by johndc on 2007-12-30
I am currently using gedit to write/edit files for POV-Ray.

The program (gedit) seems to recognize .pov files and displays using a color scheme to highlight/differentiate between comments, operatives and other syntax in the editor. However, it does not use this same scheme when editing .inc files (an .inc file in povray is like an .h file in C). these files use the same language as .pov files, so how can I tell the program to apply the same scheme to these files.

Also, I am aware that ".inc" is an extension used by other files (Pascal, java), but I don't use any of these, so I have no problem redefining ".inc" as a POV-Ray file.

I apologize if I have posted this in the wrong forum, but I had no idea where else to post it.

Thanks for your assistance!

    -John

---

### Post by erfahren on 2007-12-30
you might take a look at the gnome configuration editor (off of Applications > System Tools) or gconf-editor in the terminal)

under apps > gedit-2

there may be a way to add a string for syntex highlighting on additional file types

---

### Post by jken146 on 2007-12-30
I haven't used gedit for quite a while but I think there is a list of plugins.  You might want to check that out.

---

### Post by johndc on 2007-12-30
After poking around all the fields in the gconf editor, I came across the "syntax highlighting" option. This is apparently the feature that I am describing, though my first assumption is wrong. The editor is seeing my .pov file as a C file, and colorizing accordingly. So it seems I will have to make my own scheme if I want it to be fully POV-Ray compatible.

So now I'm off to do that. Wish me luck!

---

