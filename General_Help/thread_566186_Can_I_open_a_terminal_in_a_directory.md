---
title: "Can I open a terminal in a directory?"
date: 2007-10-03
forum: General Help
---

### Post by pat888 on 2007-10-03
In puppy Linux (I think) you can right click in a directory and you are given the option to open a terminal in that directory, is this possible in Ubuntu?

I am very new to Linux and have difficulty navigating to a terminal, opening a terminal in a directory means you don't have to navigate to it.
Pat

---

### Post by 505 on 2007-10-03
You can install this nautilus script: [http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/Open%20Terminal%20Here](http://g-scripts.sourceforge.net/nautilus-scripts/Execute/Open%20terminal/Open%20Terminal%20Here)

Make a file called 'open terminal' in the directory /home/username/.gnome2/nautilus-scripts copy the content of the above page in the file, and give it execute rights (right click file, choose, properties, tab permission, check execute.
Now you can right-click in an empty area in a folder, goto scripts, and choose open terminal.

---

### Post by vanadium on 2007-10-03
An easier option that is more "seamlessly integrated" is "nautilus-open-terminal", which you can find and install using Synaptic.

---

### Post by pat888 on 2007-10-03
> **vanadium said:**
> An easier option that is more "seamlessly integrated" is "nautilus-open-terminal", which you can find and install using Synaptic.

Thank does just what I wanted (after a restart).
Pat

---

