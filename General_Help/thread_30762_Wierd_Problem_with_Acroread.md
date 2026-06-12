---
title: "Wierd Problem with Acroread"
date: 2005-04-30
forum: General Help
---

### Post by bigblop on 2005-04-30
If I type "acro" in a shell followed by tab it autocompletes to "acroread". Then I press enter and the program opens.

But if I use Krusader as my file manager and try to open a pdf document directly I get this error:

KDEInit could not launch '/home/johs/apps/acroread/bin/acroread'

I have installed Acroread 7.0 in another directory and removed the old installation and updated my path (.bashrc) to:

export PATH=$PATH:/usr/local/Adobe/Acrobat7.0/bin

But for some reason its only my shell that recognized the path change, Konqueror, texmaker, kile seems to be using the old path.

In kile I have to type:

/usr/local/Adobe/Acrobat7.0/bin/./acroread

to use acroread as my pdf viewer.

Hope someone can help

---

### Post by jodef on 2005-04-30
> But for some reason its only my shell that recognized the path change, Konqueror, texmaker, kile seems to be using the old path. These programs are probably looking in the default paths and may have to be individually ammended to reflect the new path. 

A simpler solution might be to create a symlink to acroread in /usr/bin as follows:
**sudo ln -s /usr/local/Adobe/Acrobat7.0/bin/acroread /usr/bin/acroread**

I am also assuming you installed the program manually as on my system the installation path used by synaptic is /usr/lib/Adobe/Acrobat7.0/bin/acroread. The benefit of using the package management is that you don't manually have to create many of the symlinks that the software requires.

---

