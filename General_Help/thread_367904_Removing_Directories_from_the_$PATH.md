---
title: "Removing Directories from the $PATH"
date: 2007-02-22
forum: General Help
---

### Post by JPMaximilian on 2007-02-22
I added a directory to my PATH using this command:

export PATH=$PATH:/Users/swaroop/

How do I remove this directory from the PATH?

---

### Post by z987k on 2007-02-22
I'm not 100% on this, but I think that adds the directory to your .bash_profile in you home folder.  Open that up with gedit or whatever and see if it's in there.  Then just comment it out or erase it.

---

### Post by Ramses de Norre on 2007-02-22
If you executed that line on your terminal you can either export it again with as new value your path without the added directory, or close your current shell session and log in again.

---

