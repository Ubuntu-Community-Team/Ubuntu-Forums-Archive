---
title: "Coloring the Command Line"
date: 2007-09-15
forum: General Help
---

### Post by blithen on 2007-09-15
How do you do the color combos, and/or put a background to the Command Line.
Don't get me wrong the Command Line is cool, but I would prefer something new.

---

### Post by moore.bryan on 2007-09-15
[I]it might depend on which term you're using, but i'm not sure.  with aterm, you can just add ```
aterm*color#: name_of_color
``` to your ~/.Xdefaults file.  try it with whatever term you're using and sub-out aterm with the name of your term.
[/I]

---

### Post by machoo02 on 2007-09-15
Depends on what you want to do.  Try this one...open up your .bashrc file, and look for the section on aliases.  There are several that will enable color support for ls (to differentiate between files, folders, symbolic links, executables)

---

### Post by p_quarles on 2007-09-15
If you're using Gnome terminal (and if you're not sure, you probably are), it's pretty easy. Just right click on the open terminal window, select "edit profile," and you'll get lots of customization options. The "colors" tab will allow you to alter default text colors, and the "effects" tab will allow you to change the background color, use a background image, or make it transparent (full transparency is only possible with a desktop compositor, though).

---

### Post by Diabolis on 2007-09-18
modifying the .bashrc file works pretty good. Which language does it use or where can I learn about it? I only figured out that **\[\033[02;32m\]** changes the color of the prompt and I never saw that kind of syntax before. The way the colors have a number assigned remind me the way you pick colors in c++. Does it have any relation?

***Edit***
I just found the info I wanted in this thread: [http://ubuntuforums.org/showthread.php?t=192675&highlight=terminal+different+colors]("http://ubuntuforums.org/showthread.php?t=192675&highlight=terminal+different+colors") which linked to this page: [http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/]("http://www-128.ibm.com/developerworks/linux/library/l-tip-prompt/")

---

