---
title: "Resolution Problem on Laptop"
date: 2004-11-22
forum: General Help
---

### Post by Rossi on 2004-11-22
I have a Fujitsu Siemens Lifebook, and my fresh installation (did it twice) refuses to use the 1024x768 resolution, although we specified this in the installation.

Does anybody have any ideas as to the cause of this. We doubt it is drivers, but open to any possibilities.

Thanks in advance for any help.

Regards
~|2oss

---

### Post by randy on 2004-11-22
It's possible that the refresh rates are different or for some reason that X wants to start at a different resolution. Have you tried selecting only one resolution when you run base-config.

---

### Post by Rossi on 2004-11-22
I will try that and post back in this thread if it works or not.

Thanks.

~|2

---

### Post by Rossi on 2004-11-22
No, that did not work...

---

### Post by spirospr on 2004-11-23
I think if you reconfigure xfree should solve your problems.This could be done by doing this in console:

[COLOR=Red]sudo dpkg-reconfigure xserver-xfree86[/COLOR]

Leave most in default settings. Experiment with different settings in monitor choices till you find a solution suitable for you. After you will need to restart the xserver by pressing Ctrl-Alt-Backspace. If the server fails to restart because of falsesettings for the monitor, restart in safe mode and reconfigure the xfree in command mode by givving the same command. Write down the settings you have, before changing it, so that you can recall it if needed.

Installing the drivers for your graphic card could offer some help too.

Check what i did for my laptop in order to raise resolution.

[http://ubuntuforums.org/showthread.php?t=5464](http://ubuntuforums.org/showthread.php?t=5464)

If you solve the problem, post a reply here of what you did, so that others with same laptop will find the solution....

---

### Post by Rossi on 2004-11-23
I will try this tonight. I think I have also found the drivers too... I just need to figure out how it all works on linux. I'm a newbie :)

---

