---
title: "renaming a list of archives cutting parts of names"
date: 2007-09-15
forum: General Help
---

### Post by jomub on 2007-09-15
I have a lot of files like  ...              "[COLOR="DarkRed"]xx - la musiquita.ogg[/COLOR]" 

and I want to change all them like this  ...          "[COLOR="DarkGreen"]la musiquita.ogg[/COLOR]"

for an entire directory.

In WDWS I used dir  *.ogg -> marcar.bat , then in  'textpad' I used manual changes to do it.
Thanks (and sorry for my english)

---

### Post by vanadium on 2007-09-15
In linux, we do this the powerfull way: open the command prompt and type

rename -n 's/^..\ -\ //' ??\ -*.ogg

The -n option tells the rename command just to show how a file woul dbe renamed. It it looks like you want, then recall the command (arrow-up), remove -n and hit <enter> to rename the files.

The second parameter says how to edit the file name and follows the syntax of sed. Briefly, there are four parts in the command, separated by /. (1) s says: search/replace (2) says: what to search. This is a "regular expression": ^means: only at the beginning, the two dots mean two characters (whatever), then \[space] is a space ("escaped" using \, otherwise the shell would treat it as a separator in the command line), then - then again space. (3) You see nothing there: indeed this means "replace with nothing" (4) is empty here as well, but if you wanted to replace more than one instance, you would put g here.

The subsequent parameters list the files you want to rename. We use bash wildcards such that this expands to only these files you actually want to rename (i.e. files beginning with ## - )

---

