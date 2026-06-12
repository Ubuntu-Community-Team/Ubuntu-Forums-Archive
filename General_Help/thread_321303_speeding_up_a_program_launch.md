---
title: "speeding up a program launch"
date: 2006-12-18
forum: General Help
---

### Post by Lukich on 2006-12-18
Hi.  I have installed this 3D animation program on my Ubuntu box called Houdini.  It's running fine, but the thing that bothers me is that in order to launch it I have to go to its directory and type in "source houdini_setup_bash" and only then type in "houdini" to launch it.  I know there's a way to tie both of these commands to a single command, I think it's called "alias".  Is this feature present in Ubuntu and if so, where can I find it?
Thank you,
Luka

---

### Post by bodhi.zazen on 2006-12-18
source /full_path/to/houdini_setup_bash && /full/path_to/houdini

Or to add an alias:

Open ~/.bashrc with vim (or what have you)

Add an alias:

```
alias starth='source /full_path/to/houdini_setup_bash && /full/path_to/houdini'
```

Now in a terminal type **starth**

Call it what you will, just not houdini.

Also, you should be able to use this in your menu or as a launcher :p

Or I suppose you could add;```
exec /full/path_to/houdini &
```At the end of **houdini_setup_bash**

---

### Post by Lukich on 2006-12-18
Thanks a lot!

---

