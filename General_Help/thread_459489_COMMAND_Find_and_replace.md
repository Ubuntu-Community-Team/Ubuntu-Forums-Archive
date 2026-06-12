---
title: "COMMAND: Find and replace"
date: 2007-05-30
forum: General Help
---

### Post by Peter Sommer-Larsen on 2007-05-30
Hey I have written a report in latex and noted that one in my group have made
a spelling error. The problem is now that my latex consists of 50 different files, so I would
like to run a command that replaces the wrong word with the right word. I normally use the
command:

$ find -type f -exec grep -H 'Lithografi' {} \;

With this command I can see where the spelling errors are located, but I would be nice give
a command which could replace Lithografi with Lithography.

Any suggestions ?

THX.
Peter

---

### Post by linfidel on 2007-05-30
Sounds like a job for "sed", the stream editor.  It is especially useful for exactly this.  Unfortunately, I'm not good enough to tell you how - I usually need to experiment a bit, and maybe even ask.
But the syntax is something like this:
s/[text to find]/[text to replace with]/
You can use a colon instead of a slash, if there are slashes in the text.

Hopefully, you can figure it out, but if nobody else helps, I might be able to either answer a question, or ask my coworker tomorrow (he's left for the day).  He's pretty good with that.

---

### Post by Peter Sommer-Larsen on 2007-05-31
there must be an easier way..

can i write a program i c ? C'mon, somebody must know it..

---

### Post by fanatik on 2007-05-31
why must there be a different way? sed is the way to do it, try this:

```
$ sed -ibak -e "s/Lithografi/Lithography/" <your files>
```

this will edit in place and also create .bak's of them just in case. you can pass files to it from your find command if you want to as well.

---

### Post by Peter Sommer-Larsen on 2007-05-31
ok thx

---

### Post by linfidel on 2007-05-31
Sed is great for these things. I'm just starting to learn about it, so I'm glad "fanatik" was able to help with the exact syntax.  His idea was much simpler than I thought it would be, too, so it's a good thing he came along.

---

