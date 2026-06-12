---
title: "Re:  Gnome Terminal Title from Command Line"
date: 2015-12-07
forum: General Help
---

### Post by Jason_Hunter on 2015-12-07
I want to script the opening of gnome-terminal on login, but my first problem is setting the title of the gnome-terminal itself. 

The man page says -t will set the title, but this I'm told is obsolete when I run it. 

Any idea?

Seems also that the title changes depening on name of current tab; is this possible to disable?

---

### Post by tgalati4 on 2015-12-08
Do you want a static title or a dynamic title?  Normally, you create "profiles" with a title defined:  Edit==>Profile Preferences.  Then you can open a new terminal:

```
gnome-terminal --window-with-profile="New Title Profile"
```

I'm using *mate-terminal*, so I assume the procedure is similar to *gnome-terminal*.  My title is set to:

"What is the most important thing you need to be doing right now?"

---

### Post by Jason_Hunter on 2015-12-10
Ok, I can do that, but I don't actually see a title in there. I see a profile name, but not a gnome-terminal title name. 

I want a static title.

---

### Post by tgalati4 on 2015-12-10
Open a terminal.  Go to Edit==>Profile Preferences==>Title and Command tab.  Put in a custom title in the box called "Initial Title".  Save the profile under the General tab and call it "Custom Profile with a New Title".

At the command line, run:

```
gnome-terminal --window-with-profile="Custom Profile with a New Title"
```

---

