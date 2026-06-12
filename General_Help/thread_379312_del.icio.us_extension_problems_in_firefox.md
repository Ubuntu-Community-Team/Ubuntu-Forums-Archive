---
title: "del.icio.us extension problems in firefox"
date: 2007-03-08
forum: General Help
---

### Post by kevjaun on 2007-03-08
How do,

I'm having problems with my del.icio.us extension in firefox, ie, it doesn't work. Alas, it does nothing whatsoever! I can't tag, recall bookmarks, nadda, no reactions from any of the buttons. Any suggestions as to how I would start fixing this would be greatly appreciated.

Edgy, firefox2, del.icio.us 1.4.27

Thanks,
Kevin

---

### Post by kevjaun on 2007-03-13
B to the U to the M to the P

---

### Post by kevjaun on 2007-03-14
and here is how i fixed it....

mv .mozilla old_mozilla

synaptics>reinstall firefox

this deleted all my personal firefox info and let me start from scratch. was i happy that i had to go find and re-install all my firefox addons? no. am i happy that i can now easily access my bookmarks again? yes. do i have a suspect as to the root of the problem? installing KDE, i noted that konquerer had taken over many of the default browser roles e.g in gimp help.

there we go, kinda resolved.

---

### Post by sdyson on 2007-05-04
Glad it's not just me! Don't fancy wiping my mozilla settings so hoping someone might figure out what the problem before I do.

---

### Post by sdyson on 2007-05-05
Found a way to fix this. Just delete the extensions.* files from your profile directory. Firefox will recreate them when it starts up and then the extension should be working again.

---

