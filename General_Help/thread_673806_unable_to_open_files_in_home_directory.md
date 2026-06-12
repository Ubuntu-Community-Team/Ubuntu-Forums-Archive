---
title: "unable to open files in home directory"
date: 2008-01-21
forum: General Help
---

### Post by bigtom71 on 2008-01-21
After playing music with the totem music player, I find that I cannot open files in the home directory and cannot shut down the computer with out doing a hard boot.. Has anyone else had the same problem and if so what was the fix used to remedy the problem. This is not a big problem just a pain having to reboot to get into the home directory files.

---

### Post by banewman on 2008-01-21
Instead of a hard reboot you could try typing in a terminal
sudo shutdown -r now
and that should reboot the system.
:)

---

### Post by banewman on 2008-01-21
To check the ownership of your /home folder type - 
ls -l /home/(yourname)
in a terminal to see if that's changed and is why you can't access it.
:)

---

### Post by bigtom71 on 2008-01-21
I will try that the next time I have a problem. I did not know if that was a bug or just a problem with my system. the problem only exsists after playing music files for awhile not all the time.

---

### Post by vanadium on 2008-01-21
Perhaps this is another symptom of the issues with sound preview. In Nautilus preferences, preview tab, turn of "Preview sound files". There is a good chance that the issue will not anymore return after that. Please report back if this cured the issue.

---

### Post by bigtom71 on 2008-01-22
The suggestion about disabling the sound preview seems to have corrected the problem that I was having. Thanks for the help with this problem.

---

### Post by vanadium on 2008-01-22
Thank you for reporting back. This will likely be solved at least in the next Ubuntu upgrade.

---

