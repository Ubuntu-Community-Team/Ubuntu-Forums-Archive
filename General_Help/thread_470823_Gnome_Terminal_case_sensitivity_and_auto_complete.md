---
title: "Gnome Terminal case sensitivity and auto complete"
date: 2007-06-11
forum: General Help
---

### Post by csulok on 2007-06-11
Hey there,

Ever since I started using Ubuntu there was 1 thing that annoyed me and whenever I had to deal with it I would look for answers for days and just leave it at that..

The problem is with the Terminal that Ubuntu comes with. I can't switch off case sensitivity which drives me crazy, I have to find out how my destination is written even if I know its name. I know this could create problems whenever a folder has two similar files with different capitalization but autocomplete could help solving that. This brings me to my second problem.
It's with the autocomplete feature which is kinda annoying too, instead of autocompleting the filename for single <tab> press, it lists the available choices. It would be much better if it cycled through the available choices for single <tab> press and list the available ones for example on double <tab> press.

Is there a way to switch off case sensitivity in the terminal? 
Is there a way to cycle through instead of listing the available choices when using the autocomplete feature?

Any help is very much appreciated :) Thanks for reading

csulok from Hungary

---

### Post by stylishpants on 2007-06-11
Your problems are actually with the bash shell, and with the readline library that provides line editing functionality.  See the bash and readline man pages for more information.

> 
Is there a way to switch off case sensitivity in the terminal? 


Create (or edit) a file named '.inputrc'  in your home dir.  Inside it put this line:
```

set completion-ignore-case On

```
After you do this, all new shells that start up will have case-insensitive competion.
You can also hit Ctrl-x Ctrl-r to get your current shell to re-read this file and get the change too.


> 
Is there a way to cycle through instead of listing the available choices when using the autocomplete feature?

Run this command in your shell to get this behaviour for that shell only.
```
bind '"\C-i": menu-complete'
```
If you like how that works, then add that command to your ~/.bashrc file so that future shells will use that behaviour too.

---

### Post by hikaricore on 2007-06-11
*borrows case-insensiive solution*

Wow that had been annoying me forever.  :)  thanks.

---

### Post by csulok on 2007-06-22

thank you :) i love you \o/

---

