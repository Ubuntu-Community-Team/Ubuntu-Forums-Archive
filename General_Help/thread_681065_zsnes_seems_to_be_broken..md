---
title: "zsnes seems to be broken."
date: 2008-01-28
forum: General Help
---

### Post by onesojourner on 2008-01-28
When I try to open zsnes from the menu it pops up for about 2 seconds with a black screen and then it disappears. When I try to open it from the terminal I get this.

```

Creating link /home/peter/.kde/socket-peter-laptop.
can't create mcop directory

```

---

### Post by 47_MasoN_47 on 2008-01-28
I could be wrong, but isn't zsnes a Gnome app?  I haven't ever used KDE but maybe it is the problem?  It works fine in my Gnome environment.

---

### Post by fredmv on 2008-01-28
I had the same problem.  All you have to do is create the directory.   

From the terminal, do this  (assumes you are in your home directory): > cd .kde
mkdir socket-peter-laptop

Then launch ZSNES and it should work fine.  For some reason, it seems as if the automated script can't do it.

---

### Post by onesojourner on 2008-01-28
that did it. thanks.

---

### Post by onesojourner on 2008-01-28
I do have one more question though. To this point I have been running 2 seperate commands.

cd xwii

and then

./xwii profiles/classic.xwii

how can I do both of those in one command. I want to create custom launcher.

---

