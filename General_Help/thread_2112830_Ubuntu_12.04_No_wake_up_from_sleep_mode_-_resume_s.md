---
title: "Ubuntu 12.04 No wake up from sleep mode - resume /suspend issues"
date: 2013-02-05
forum: General Help
---

### Post by pouchette on 2013-02-05
[EDIT] > I did upgrade the solution for better results <

Problem :

For me, the issue is on HP Pavilion Dv7 (and other many laptops I noticed), there are 2 annoying issues ; no wake up (resume) from sleep mode, and no shut down properly.
Have to hard reboot...

Ati/Amd graphic card for me (not tested on Nvidia but could work may be)

After reading several posts to fix it, and tried many many proposals that didn't work for me, I finally found a solution (till new updates or kernel will fix it a better way, we hope).

This problem comes from a lake a video quirk database for some pc

Here is what to do for make it work :

- Method with graphical super user mode :

Open Terminal console and type :

**sudo nautilus** - you'll be asked to type your password (it will open your home folder with sudo permission) 

1) From that folder, browse to go and open the directory : system file, usr, lib, pm-utils, **sleep.d**
(system file/usr/lib/pm-utils/sleep.d)

> then remove/delete the file "98video-quirk-db-handler" that you'll find into that folder

(before removing it, drag and drop it to your desktop to keep a copy of it in case this didn't work)


2) Now, browse and open the directory : /etc/pm/**confid.d**

> We have to edit a file in this directory

> open and edit a text file on your desktop that you name ADD_PARAMETERS

> type this line into the text file :

ADD_PARAMETERS="--quirk-s3-mode --quirk-vga-mode-3 --quirk-s3-bios --quirk-radeon-off " (including the quotes)

[NB : if you want to try this with Nvidia Card don't add -quirk-radeon-off]

> Save it on your desktop and close it (with the name ADD_PARAMETERS)

> then Drop the text file from desktop into the folder /etc/pm/**config.d**

(verify permissions of the file on "properties - permission menu" it has to be on root "read and write" for all 3 options)

Close the folder

reboot (or close session)

Done ! 

(Of course you can do all this procedure in a terminal console with root permissions)


It really works perfectly ! wake up from sleep mode and shut down properly !!


NB: not sure- but if upgrade of fglrx (ati driver) or getting a new pm-utility package from the update manager you might have to do this again, except if the updates did fix the issue :-)

That's it.

If you have any questions or miss succeed in one of the process feel free to ask :-)

---

