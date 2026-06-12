---
title: "nautilus action for latex"
date: 2007-11-16
forum: General Help
---

### Post by hendrikwout on 2007-11-16
Hi,

I'm trying to make a nautilus-action for pdflatex but it doesn't work well with spaces in directory names. Here is what do:

In the nautilus action dialog, I fill in:

Path: gnome-terminal
Parameters: -x pdflatex '%M' 

When I open the actio with a .tex-file, I look into the process manager and I see that the quotes don't show in the command: the command looks like

gnome-terminal -x pdflatex /path/to/directoryname with spaces/file.tex

but it should be:
 gnome-terminal -x pdflatex '/path/to/directoryname with spaces/file.tex'

Anyone can help?

Thx in advance.

---

### Post by hendrikwout on 2007-11-16
Found it at last:

the parameter chould be:
-e="pdflatex -output-directory %' %d %' %' %M %'"

:popcorn:

---

### Post by bhishma on 2008-02-07
Thanks.  This was a great help.

I made an action for *.tex files using the rubber LaTeX wrapper ('rubber' package).

Path: gnome-terminal
Parameters: -e="rubber -f -d %' %M %'"

---

