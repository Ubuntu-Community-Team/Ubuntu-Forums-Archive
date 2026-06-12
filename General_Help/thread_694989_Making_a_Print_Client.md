---
title: "Making a Print Client"
date: 2008-02-12
forum: General Help
---

### Post by Shyper on 2008-02-12
Hey, I'm currently attempting to make a Linux GUI print client for a bunch of people I know. I have it running as a standalone client that can print postscript files to the several printers our network, but I want to make it a bit more user-friendly: I'd like for the client to show up as a printer in the native "Print" menus of most applications. Printing to this printer will bring up the GUI client and allow the user to use the client to print the application he just tried to print. Doing this all natively on Ubuntu is a big pain-in-the-butt for various reasons, mostly due to our network; this is why I've created the custom GUI client. Anyway, this is what I have so far:

- Create a 'dummy' printer in CUPS that the user can print to.
- Make it so that whenever the user prints to this 'dummy' printer, it just prints a postscript copy to [file] at [path].
- Create a daemon that brings up the client whenever it senses a new/changed postscript [file] at [path].
-??? 
-Profit!

So, I know how to implement Steps 1 and 3-5: Step 2 is what's bothering me. How can I create a CUPS virtual printer that will print a postscript file of the item just printed with a given name to a given path? Thanks a lot in advance.

---

### Post by Shyper on 2008-02-12
Bump.

---

### Post by Shyper on 2008-02-12
Bump again. Sorry, I've tried googling this for an hour, and nothing's come up.

---

