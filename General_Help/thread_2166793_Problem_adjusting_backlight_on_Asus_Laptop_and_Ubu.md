---
title: "Problem adjusting backlight on Asus Laptop and Ubuntu 13.04"
date: 2013-08-11
forum: General Help
---

### Post by jose_rojas2 on 2013-08-11
I have a problem adjusting the backlight on my Asus U46E using the keyboard hotkeys, I am only able to choose between 91 and 98 percent it does not increase or decrease further. I've tried setting kernel flags like  "acpi_backlight=vendor" and "acpi_backlight=legacy" along with "acpi_osi=linux" but none of these have worked, setting the brightness manually from system settings does work, although such setting gets reset on reboot. 

I tried installing the latest intel linux drivers and echo'ing an integer to /sys/class/backlight/intel_backlight/brightness does change the brightness correctly, but the system seems to be using /sys/class/backlight/acpi_video0/brightness how do i force the kernel to use intel_backlight? 

I've also tried configuring events for these hotkeys using acpi_listen and /etc/acpi/brightness.sh called by /etc/acpi/events/brightness, but this did not work either.

I'm editing this to report that xbacklight does seem to be working, although I'm not sure what it does to change the brightness. I've also tried running a shell script with inotifytools which monitors changes to /sys/class/backlight/acpi_video0/brightness and then modifies /sys/class/backlight/intel_backlight/brightness with the corresponding value but this didn't seem to work either since the problem seems to be in whatever the hotkeys are calling when pressed


[B]SOLUTION

[/B]I've managed to temporarily fix my problem, the solution was adding these lines to /etc/rc.local
**WARNING:**You won't get the right brightness measurement on the brightness popup nor you will be able to change the brightness from the system settings panel, only Fn Hotkeys will work with this method

```

chmod -r /sys/class/backlight/{wrong backlight directory}/max_brightness
chmod -r /sys/class/backlight/{wrong backlight directory}/brightness
chmod -r /sys/class/backlight/{wrong backlight directory}/actual_brightness

```

replace "{wrong backlight directory}" with whatever folder suits your situation.
[B]THIS SOLUTION WILL ONLY WORK IF YOU HAVE TWO FOLDERS UNDER "/sys/class/backlight/"
OR ELSE YOU WILL FIND YOURSELF WITH NO WAY OF ADJUSTING THE BACKLIGHT

PS. Make sure the other backlight folder does work when you press the Fn+Brightness up or down, if it doesn't research on how to edit ACPI events so you can add the hotkey there[/B]

---

### Post by jose_rojas2 on 2013-08-15
I've managed to solve the problem, at least with a temporary fix

---

### Post by ajosmer on 2013-09-11
I have come upon a permanent fix.  I installed boot-repair onto my permanent Linux installation (Linux Mint 15), and ran it.  However, instead of just running the default fixer, like what is required to install the EFI GRUB to begin with, I went to advance settings.

Under the "GRUB options" tab, I checked "Purge GRUB before reinstalling it" and "Add a kernel option:", which I set to "acpi_osi=".

As boot-repair ran, it eventually popped up a warning saying "buggy-kernel detected" and asked if I wanted to backup and rename all the Windows EFI files.  I clicked "Yes" this time, whereas I hadn't before.

I don't know which of these things fixed the issue, but when I rebooted, the backlight buttons worked perfectly again, as I had gotten them to on Linux Mint 14.  My guess is that installing GRUB with the blank "acpi_osi=" statement from the get-go configures something slightly differently, but I don't have any substantiated theories.

Hope this helps, let us know!

---

