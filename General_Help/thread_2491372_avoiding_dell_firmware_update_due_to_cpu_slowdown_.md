---
title: "avoiding dell firmware update due to cpu slowdown - updater always ticks checkbox"
date: 2023-10-05
forum: General Help
---

### Post by lorriman2 on 2023-10-05
A recent security update for intel cpus means a huge performance slowdown for older intels like mine. So I've avoided it as I believe I don't need it; rather as spectre etc really only applied to servers. 

Dell's own firmware update is irreversible, it blocks these kinds of security update from re-installing prior firmwares. And has no options in the BIOS config for disabling the patch/microcode to restore performance. 

What I've learned, just in time, is that the Ubuntu updates can carry the firmware update also.

I have uninstalled the firmware updater,  [COLOR=#4D5156][FONT=arial]fwupdmgr, [/FONT][/COLOR]and as a precaution unticked the auto updates. 

The Ubuntu sofware updater app shows the firmware ready to be downloaded. Presumably also restoring the firmware updater. 

But unticking it doesn't carry over to the next time it appears?!?!?!?! Which is pretty much every day. 

Is there any way to permanently disable this?

---

### Post by Dennis N on 2023-10-05
If there is some package you don't want Software Updater to update, you mark the package as a hold. This is done in the terminal:
```
sudo apt-mark hold packagename
```
Like:
```
sudo apt-mark hold fwupd
```
In future updates with Software Updater, it will remain unchecked.
You can use wildcards to mark several related packages to hold. For example:
```
sudo apt-mark hold libreoffice*
```
To reverse a hold, use unhold.
See the apt-mark manpage for more info.

---

