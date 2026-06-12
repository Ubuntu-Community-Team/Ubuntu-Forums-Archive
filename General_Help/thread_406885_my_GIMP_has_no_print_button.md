---
title: "my GIMP has no print button"
date: 2007-04-11
forum: General Help
---

### Post by gregtomko on 2007-04-11
I am new to linux and I am trying to print an image in the gimp image editor.  There is no "print" selection under the file menu in gimp.  It has all the other options, but it doesn't say "print" anywhere.  It is not that it it greyed out, it just isnt even there at all.   I can print through firefox, and openoffice, and the standard image viewer, and my printer seems to work fine and setup quite easily, but in gimp there is no print option.  What can I do?

---

### Post by Maestro23 on 2007-04-11
Need gimp-print plugin.

> sudo aptitude install gimp-print

or open Synaptic(GUI) and search "gimp-print", mark for installation.

If you don't find it, you need to enable extra repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by gregtomko on 2007-04-11
I used synaptic to install the gimp-print and also gutenprint, and tried restarting, but it still has no print option.  could installing both packages be the problem?

---

### Post by ginnie6 on 2007-04-11
I had this same problem and I fixed it by uninstalling and reinstalling from synaptic.

---

