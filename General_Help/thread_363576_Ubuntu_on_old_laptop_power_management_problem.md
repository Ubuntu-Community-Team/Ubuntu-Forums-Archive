---
title: "Ubuntu on old laptop power management problem"
date: 2007-02-17
forum: General Help
---

### Post by smashmouth on 2007-02-17
Hello there. I have installed Ubuntu on a Compaq Armada m700 Notebook PC old PIII notebook.

The OS is working great apart from I can't stop the system from hibernating/screen closing when the lid is closed.

I have changed the settings under power management so that it shouldn't do this, disabled the screen saver and checked the BIOS that it doesn't have any power saving/screen closing settings enabled (there weren't any).

I have tried a couple of boot comands too e.g. acpi=none & acpi=force but to no avail.

Any ideas?

Thanks in advance

Linux noob

---

### Post by DagMan on 2007-02-17
try typing 'gconf-editor' in a terminal and in apps-gnome-power-manager make sure action_battery_button_lid and action_ac_button_lid are set to none or to what value you want.  Highlight them for a description in the lower pane.  These values should be set when you use the power manager interface though so this may not be the solution.

If that doesn't work, and this may be specific to my laptop as there are various packages that get selected for isntallation.  On mine, there is a script called lid.sh in /etc/acpi which handles what happens when the lid is closed.  Perhaps if you want nothing to happen when you close the lid, you can rename that script to lid.sh-bak or something and see how that goes.  If that does work and you want your lid to blank the screen then have a look at all the scripts in /etc/acpi and see if there is one called screenblank.sh and what it does etc etc.  Make sure you backup anything you change so you can undo it if it does not work out.  

If you want more help with trying this or want to be walked through it a bit more than the very general help I posted then just say the word and I'll try to come back if someone else does'nt get to it first.

first though, see if these scripts even exist
```
ls /etc/acpi/lid.sh
ls /etc/acpi/screenblank.sh
```

If they exist, try to run them like this and see what they do, if anything:
```
sudo /etc/acpi/lid.sh
sudo /etc/acpi/screenblank.sh
```

---

### Post by smashmouth on 2007-02-17
Thanks a lot for that DagMan, I will try it when I get into work on monday and let you know.

---

