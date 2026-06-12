---
title: "Ubuntu 18.04 unable to open/save files"
date: 2018-06-29
forum: General Help
---

### Post by acoad on 2018-06-29
Hi,
This is a new install of 18.04 on a Macbook Pro machine. I am unable to open or save files from within applications. Two examples:

 - Atom editor - File->OpenFile... hangs Atom. The screen darkens but no file dialog is shown. The only way forward it to kill Atom via System Monitor
 - Firefox - downloading a .png file displays the file within Firebox. Right clicking and Save Image... hangs Firefox - the Firefox window darkens but no file dialog is displayed. The only way forward is to kil Firefox via the System Monitor

In both cases, I have checked to see if the file open or file save dialog is being displayed off screen in another workspace - it is not.

Any suggestions would be welcome.

Regards,
ac

---

### Post by acoad on 2018-06-29
SOLVED: the problem was that 18.04 had configured two screens when there is only one - I guess that the File Open/File Save dialog was being displayed on the second non-existent screen... While I checked that possibility in Activities, the dialog did not show up in the sidebar so I guess only main windows are visible...

When I changed the configuration from two screens to one screen in Settings, the confirmation dialog "Do you really want to save changes.." did not show up so my change was not in fact saved. Rebooted. Tried to change the screens in Settings again and this time the confirmation dialog showed up and I was able to save a one screen config.

All is fine now.

ac

---

