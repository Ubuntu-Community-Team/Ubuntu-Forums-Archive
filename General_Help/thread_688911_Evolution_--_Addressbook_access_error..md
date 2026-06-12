---
title: "Evolution -- Addressbook access error."
date: 2008-02-05
forum: General Help
---

### Post by mivo on 2008-02-05
For some time now I experience a problem with the local addressbook in Evolution. New contacts cannot be added, no contacts are added automatically, and when I open it, I get an error message saying: "Error loading addressbook. Please check that the path /home/username/.evolution/addressbook/local/system exists and that you have permission to access  it."

The path exists, and my username has read/write access to it (as well as to the .db and .summary files in there). I've tried re-installing evolution, deleting the addressbook files (the default ones were recreated), checked the keys in Gconf-Editor, restored everything from a backup. Nothing fixed it. The problem started after I backuped (using the option within Evolution) on a previous installation, re-installed Gutsy, and restored the backup). Only pointer I have is that in .../local is not also /system, but also an empty directory named 1201319153.14627.5@calico (calico being the machine's name).

Google didn't yield any relevant or recent information. If anyone has any ideas, I'd be grateful. :) Thanks in advance!

PS. Of note is that the addressbook.db file was last modified on Nov 3 (this was before reinstalling Gutsy),  and last accessed just now. So, it -is- being accessed, in which case Evolution's error message may be misleading.

---

### Post by mivo on 2008-02-11
I'm still unclear what the error was caused by, but I figured out a fix. Just posting this here in case someone else runs into the same trouble. :) The following steps will get the malfunctioning addressbook going again:

- close Evolution
- delete /home/username/.gconf/apps/evolution/addressbook (it will be recreated)
- delete /home/username/.evolution/addressbook (it will be recreated)
- reboot your computer (this is crucial, otherwise the faulty gconf files will be restored)
- launch Evolution and enjoy your working address book

The important step I missed in my previous attempts to fix this trouble was restarting the computer. It dawned on me when the same, faulty gconf files were recreated even after deleting everything and restarting Evolution. Apparently Gnome keeps the settings in the memory.

---

### Post by NIT006.5 on 2008-02-11
Useful to know. Many thanks.

---

### Post by jasonbell on 2008-02-29
Awesome!  I only just found this and it has saved me.  I have been suffering with no addressbook for weeks!

---

