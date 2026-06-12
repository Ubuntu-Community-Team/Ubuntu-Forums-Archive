---
title: "Sleep Button on Thinkpad T43p"
date: 2007-07-13
forum: General Help
---

### Post by ehula on 2007-07-13
My problem is that Fn-F4 won't put my Thinkpad T43p to sleep, but I am able to put it to sleep by selecting "Suspend" from the logout options, and from "Suspend" in the Power Manager icon in the Notification Area.

I have installed uswsusp and can successfully suspend with "sudo s2ram".

Could my problem be tied to /etc/acpi/suspend.sh? I have edited this file in the past, but I think it is back to it's original state.

Any help is greatly appreciated.

---

### Post by ehula on 2007-07-17
bump

---

### Post by UJoe4 on 2007-07-17
First, look to see whether there are any "sleep button" or "suspend button" options in your GUI power manager. If you're using KDE, the power manager it ships with (kde-guidance-powermanager) has very few options, so try to install kpowersave and see if it has them.

If none of those options are present (or they are but don't do anything), it might be a bit more complicated. On my Thinkpad the Fn+F4 combination calls "/etc/acpi/sleepbtn.sh". Test and see if it does on yours too by adding:
> echo > /home/**yourusername**/doesitwork.txt
to the beginning of "/etc/acpi/sleepbtn.sh". Then press Fn+F4 and check whether it's created the file "doesitwork.txt" in your home directory. If not, then maybe check whether you have the right keyboard layout set, whether the other Fn keys work, etc.

If it does create that file then you know it's calling the right script, so you just have to modify that script to make it do what you want. My sleepbtn.sh file contained:
> #!/bin/bash
. /usr/share/acpi-support/key-constants
acpi_fakekey $KEY_SLEEP
which, like you, didn't actually put the laptop to sleep. So I added "/etc/acpi/sleep.sh" to the end of that file, and now it works.

If that doesn't work for you, maybe try changing some of the actions in "/etc/acpi/sleep.sh" itself (after backing it up, of course). For instance, it exits immmediately if gnome-power-manager or klaptopdaemon are running so that they can handle it. Then, it runs the scripts in "/etc/acpi/suspend.d" in order, and on resume it does the same for the scripts in "/etc/acpi/resume.d". Also, there may be issues regarding whether or not it locks the screen (requires a password) on resume. Post back if there are problems.

---

