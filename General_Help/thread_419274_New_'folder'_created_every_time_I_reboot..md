---
title: "New 'folder' created every time I reboot."
date: 2007-04-22
forum: General Help
---

### Post by Necreia on 2007-04-22
Every time I reboot the computer, a new file with a funky name is created in my home folder.  They are the 4 below with the weird characters.
 
Here is a screenshot of it: [[IMG]http://img172.imageshack.us/img172/7134/screenshotbv8.th.png[/IMG]](http://img172.imageshack.us/my.php?image=screenshotbv8.png)

I don't know where to begin looking for the source of such a strange issue, any ideas?

Edit: It MAY be related, but the gnome panels won't load the first time I start my computer.  I have to ALT+CTRL+Backspace and re-login in order for them to show.  When I do that I see a message that must complete before it'll return to login screen that hangs on "Checking Battery State..." for about ~20 seconds.  [Which is weird, this is a desktop without a battery].

---

### Post by gamma on 2007-04-22
Very weird. Are you running any applications besides the default set included in Ubuntu? Are the folders empty? Are you shutting down the machine properly each time?

---

### Post by Necreia on 2007-04-22
I'm running a clean install of 64bit feisty fawn + beryl + quicksynergy (that's it).

I suspect the panel/gnome issue could have something to do with Beryl, but not sure how/what to check for that.

I'm shutting down properly (not pushing button, selecting shutdown or restart and waiting for it to finish).

Edit: I uninstalled powernowd because of an issue with my core 2 duo, could that effect the ""Checking Battery State..."?

---

### Post by Necreia on 2007-04-23
OKAY!  I found the problem.

A file is created every time I start QuickSynergy (what the heck?).  I pulled it from the add/remove, do I submit this as a bug in the launchpad even though it's not ubuntu itself?

Very weird...

---

### Post by traffas on 2007-04-23
I, too, experience the spontaneous creation of these folders with weird characters in my home directory. Does anyone know how to prevent this or where to submit a bug to QuickSynergy?

---

