---
title: "Warning when menu.lst is changed?"
date: 2007-11-13
forum: General Help
---

### Post by kokaku on 2007-11-13
I'm running Gutsy and have the common problem that sometimes something updates menu.lst and removes the Windows boot config. No problem, I know how to fix that. What I'd like to know is this - is there a way I can be alerted that something updated menu.lst *before* I restart and find out the hard way? Is there a log file that would show this or utility to monitor file changes or some other idea? Ideally, following the update, a notification dialog would alert me so that I can edit the file.

Thank you

---

### Post by geirha on 2007-11-13
It shouldn't remove your windows entry like that. Could you post your menu.lst with the windows entry?

When grub needs to be updated, the update-grub script will be run. If you run this yourself after editing menu.lst, and it doesn't remove anything it "shouldn't", your menu entries should be safe. So always run ```
sudo update-grub
``` after editing menu.lst, to confirm that your changes are ok. And if you accidentaly delete menu.lst, update-grub will create a new one, though only with ubuntu entries ...

---

