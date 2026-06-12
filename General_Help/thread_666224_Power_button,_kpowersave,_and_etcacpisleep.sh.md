---
title: "Power button, kpowersave, and /etc/acpi/sleep.sh"
date: 2008-01-13
forum: General Help
---

### Post by ocwo92 on 2008-01-13
I'm having problems getting kpowersave to accept a command-line execution of /etc/acpi/sleep.sh, so I'm looking for some kind of work-around.

My goal is to have a Kubuntu media computer that suspends to ram when not in use. This means that if the user presses the power button, the computer should suspend-to-ram. I can accomplish that with kpowersave.

The computer must also be woken up regularly by a remote computer that performs some administrative tasks, and then go back to sleep. I've managed to get this to work by calling /etc/acpi/sleep.sh as the last step in the script.

Each of these two methods work by themselves, but once kpowersave is running, apparently the /etc/acpi/sleep.sh script no longer puts the computer to sleep; in fact, this script appears to do nothing at all. If I shut down kpowersave, the script works again, but then a power button press means shut-down, not sleep.

Can anyone suggest a method to cause a power button press to put the computer to sleep without voiding the /etc/acpi/sleep.sh functionality? Alternatively, can someone suggest a different command line option that can put the computer to sleep while kpowersave is running?

(I'd rather not echo down into /proc/acpi/sleep, unless someone can convince me that it causes the proper shutdown and startup scripts to execute.)

---

