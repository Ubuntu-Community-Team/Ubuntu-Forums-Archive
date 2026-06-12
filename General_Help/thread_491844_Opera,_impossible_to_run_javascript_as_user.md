---
title: "Opera, impossible to run javascript as user"
date: 2007-07-04
forum: General Help
---

### Post by fantan on 2007-07-04
Hi Everybody,

Some days ago I Installed a Feisty Fawn system and the Opra browser on it.

The problem is, that when i want to run Opera as user, it doesn't want to navigate to links like for example this: "javascript:link("http://www.portfolio.hu/tozsde/index.tdp",33)"
But, when I start Opera with sudo, then everything is OK.

In this case, when I start Opera with sudo, then it uses the directory of root, and this is very confusingly.
Of course in Opera I've enenabled also the plugins, the javascript and java too.

The other strange thing is that some weeks ago I've installed the Feisty system from the same installation disc and Opera from the same package on other computers too, but there weren't problems with Opera at all.

Can anybody tell me, what to do?

Thank you wery much in advance.

fantan

---

### Post by kerry_s on 2007-07-04
if you used sudo, then you probably screwed up your ~/.opera permissions. graphical applications should be launched with "gksu" or "gksudo". sudo is only to run commands as root in terminal.

you can try to fix your permissions for the .opera folder or just delete it and start a new.

to get to the .opera folder, open nautilus and press ctrl+h to show the hidden folder's/files. if it don't let you use root(gksu nautulis) to make the changes or delete.

---

