---
title: "Xubuntu 13.10 keeps freezing after screen goes to sleep"
date: 2013-11-22
forum: General Help
---

### Post by sciencegeek on 2013-11-22
I recently installed Xubuntu 13.10 on my desktop because Manjaro 0.8.x suddenly became unbootable and I decided to switch to something more stable.  I kept my previous /home directory when I installed the new Xubuntu installation.

Anytime I am away from my computer awhile the screen goes to sleep and when I try to wake it back up it refuses to wake back up.

I am fairly new to linux so I do not know what sort of commands to enter at the command-line in order to attempt to troubleshoot the problem or pull up an event log.

Can anyone help me with this issue?

Thanks

---

### Post by Toz on 2013-11-22
Hello and welcome to the forums.

Perhaps you can provide some more information about your computer - specifically the make and model. Try running the following command on a terminal window and posting back the results - it will tell us about your video card(s):
```
lspci -k | grep -iA2 VGA
```

Have you determined whether the system goes into suspended mode or does the screen just blank (screensaver)? If its suspending, there would be log entries being made in the /var/log/pm-suspend.log file.

Is the screensaver enabled? Have a look at Settings Manager -> Screensaver. What are the settings? Try unchecking the "Fade In" and "Fade Out" options to see if that helps (assuming that its just a blank screen issue).

---

