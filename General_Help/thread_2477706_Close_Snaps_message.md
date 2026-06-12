---
title: "Close Snaps message"
date: 2022-08-04
forum: General Help
---

### Post by sotires on 2022-08-04
I constantly get a message that Snaps needs to be updated and I have x days left to do it, so I should close Snaps. 

I didn't even know that I had opened Snaps. 
How do I close it? All the google search comes up with how to uninstall snaps, not how just to close it. 
Thanks.

---

### Post by Holger_Gehrke on 2022-08-04
'snap' is a package system. Various Programs can be installed from / as snaps. The message should actually tell you what program it wants to update. One obvious candidate is Firefox, which is installed as a snap by default on new Ubuntu versions. You can either close Firefox and wait a few hours (snap tries to update 4 times a day ...) or you can close Firefox, open a terminal and enter 'snap refresh firefox' to start the update manually.

Holger

---

### Post by grahammechanical on 2022-08-04
I get that message on Ubuntu 22.04 when I open Firefox. I ignore it. When the specified number of days has passed Firefox will update without the user needing to run Software Updater. That has been my experience. And I run Software Updater every time I load Ubuntu 22.04. It is the first action I take.

[https://askubuntu.com/questions/1412140/pending-update-of-firefox-snap-close-the-app-to-avoid-disruptions](https://askubuntu.com/questions/1412140/pending-update-of-firefox-snap-close-the-app-to-avoid-disruptions)

I am guessing that many business employees do not shutdown their machines and do not close Firefox and do not update the system. A web browser that is not up to date is a security vulnerability.

Regards

---

### Post by mIk3_08 on 2022-08-05
> **sotires said:**
> I constantly get a message that Snaps needs to be updated and I have x days left to do it, so I should close Snaps. 

I didn't even know that I had opened Snaps. 
How do I close it? All the google search comes up with how to uninstall snaps, not how just to close it. 
Thanks.
This is what the UF community is fighting for that Firefox should be remove from snaps. I been encountering this discussion before in some UF thread. Now it is so very obvious that snaps is making inconvenient moves to the user of Linux Ubuntu Operating System. I think this is the time that Firefox should be remove from snaps. Regards and cheers.

---

### Post by arraybolt3 on 2022-08-07
If you want to get that message to go away for a bit, you can force-update all Snaps with the command line. Make sure to close Firefox or whatever other application(s) are nagging you about updates (or for safety's sake you can also just close all open apps if you're not sure which ones need updating and which ones don't). Then open a terminal with Ctrl+Alt+T, and run:

```
 sudo snap refresh 
```

This will update all of the Snaps on your system.

If you want to only just update Firefox and whatever Snaps it depends on, you can also do:

```
 sudo snap refresh firefox 
```

---

### Post by Dennis N on 2022-08-07
If you use Software Updater, snaps will be checked for updates and updated whenever you have updates of other packages. If you use apt in the terminal, then they don't get updated with you regular updates. One reason you might want to rely on Software Updater to handle updates.

Possibly because I do use Software Updater, I've never seen messages about snaps needing to be updated.

---

