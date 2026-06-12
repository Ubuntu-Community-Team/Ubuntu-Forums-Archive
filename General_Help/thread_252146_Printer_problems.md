---
title: "Printer problems"
date: 2006-09-06
forum: General Help
---

### Post by Coomkeen on 2006-09-06
Printer problems

I have a HP PSC500 with a Netgear print server (PS101), on a windows network in a 'workgroup'.
It works fine from windows.
On setting up the printer from Ubuntu, at step 1 of the 'Add a Printer' I select Network Printer, and Windows Printer, and immediately a small window pops up asking for the workgroup's user name and password.
As far as I know it doesn't need either, but I've tried leaving both blank, and putting in my login and password.
Both methods seem to work in that after all the other steps the printer gets installed.
But it doesn't respond to a test page print.
Nothing happens at all at the printer, and eventually it lists the printer a 'stopped'.

If I check under the printer properties it gives the host (PSD6BF29) and the printer (PSC500) and the user name and password are blank.

If I look under the network file browser, the Windows Network appears OK. Double-clicking that gives the workgroup. Double-clicking that gives my computer and my wife's computer, and the Netgear Printer Server (PSD6BF29).
If I select 'properties' from a right-click, and select the 'permissions' tab, they are all read only.
Trying to select 'write' gets a 'The permissions could not be changed' message.
This happens when I'm logged in as root as well.

Is this a Ubuntu, Linux, or Windows problem?
Most likely my duff setting up!
And whatever it is, what's the solution?

Any help appreciated.

---

### Post by DoctorMO on 2006-09-06
It might be worth investigating CUPS ability to set up windows printers. you can either configure your network printer via the CUPS service page via a browser. or you can learn how to configure cups via config files.

But the best option is to post a message to the CUPS forums/message boards and when yoyu find the anwser remember to post what you did to get it fixed.

sorry I couldn't be of more help, I do know that some printers (Xerox ect) have cups built in (I wish windows had cups support because it's so much easier to set up)

---

