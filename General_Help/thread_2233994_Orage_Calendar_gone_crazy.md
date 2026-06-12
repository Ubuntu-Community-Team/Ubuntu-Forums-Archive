---
title: "Orage Calendar gone crazy"
date: 2014-07-11
forum: General Help
---

### Post by JKyleOKC on 2014-07-11
I use the Orage calendar to keep track of bills to be paid, and doctors' appointments, so it's pretty critical to me.

As of this evening, it has become almost unusable -- while mousing over its icon in the notification area still shows the next five upcoming events, launching the full calendar window by double-clicking that icon shows no events at all.

I've verified that the actual event file in ~/.local/share/orage is still there, intact, and has proper permissions. I've verified that the oragerc file still points to that same event file. I've re-installed the program via Synaptic. The problem, however, remains. I'm at a loss to determine the next steps in troubleshooting this! I've attempted to add a test event to see whether the actual alarm will still work, but the "save and close" command does nothing. Attempting to close after the attempt to add an event brings up a "Mother may I?" window warning that new data will be lost if I proceed, but no "save" commands have any effect. It acts as if the file's write permission has been cleared, but the properties display still shows permissions as "read and write" for the owner, me.

Pertinent version data: Xubuntu 12.04.4 i386, with no recent updates that appear pertinent to the issue although I've not tried rolling back to the previous kernel yet. The XFCE package is 4.10 from the PPA rather than the 4.8 originally distributed for Precise, but again no recent updates. The help file with the package has not been updated since 2010 and bears little resemblance to the current program's UI.

Anyone have any ideas to help get this working again?

---

### Post by JKyleOKC on 2014-07-13
bump

copied the ICS file to another system running the same o/s and calendar version, and that one works perfectly; has to be something gone wrong with the program file or possibly a library, but reinstallation didn't help.

---

### Post by Toz on 2014-07-13
Try running orage from a terminal prompt and have a look at the messages that are printed to the terminal window when you start the program and when you try to save an event. Perhaps something will be printed to help troubleshoot the issue.

---

### Post by JKyleOKC on 2014-07-13
Many thanks, Toz! I should have thought of that; I guess I've become brainwashed to the GUI after all these years!

It turned out to be four "foreign files" that I had deleted from my Downloads directory because their appointment times were past, but they were still in the .config/orage/oragerc file and of course could not be found during the program's starting actions. Manually removing them from the oragerc file put everything back to normal once more.

At least along the way I discovered orage's "archiving" function and am now using it to keep the working calendar file to a reasonable size rather than holding more than 5 years' worth of expired appointments...

Thanks again!

---

