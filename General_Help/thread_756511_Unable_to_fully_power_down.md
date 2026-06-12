---
title: "Unable to fully power down"
date: 2008-04-15
forum: General Help
---

### Post by SirPerigrin on 2008-04-15
A simple problem. When i use any form of a shutdown command be it the GUI shutdown buttons or "Sudo shutdown -Ph now" or any other variations of the command line the system simply will not halt. The system is a Sony Vaio PCV RX650 Desktop. Its used as a web/e-mail machine for my family and is but one of a half doezen Ubuntu machines in the house. At the moment it is using KDE 3 but the problem existed under Gnome. No errors occur, it just starts to shut down, and when the progress bar on the shutdown splash gets to the end, it stops. Screen stays up displaying the empty progress bar and the Kubuntu logo. 

I'v tried everything short of recompiling the kernel or flashing Bios. The motherboard IS softpower and does work under XP Home. [K]ubuntu is the only OS with the issue. I honestly can't even think of a place to start troubleshooting this or even find debug data... 

ANY help is appreciated as even a wrong idea can start me off towards the right solution.

EDIT: the command acpi_available ; echo $? returns a value of 1, i think this MAY be relevant and part of the problem, but i have no idea how to fix it.

---

### Post by Flying caveman on 2008-04-15
[http://ubuntuforums.org/showthread.php?p=2595626](http://ubuntuforums.org/showthread.php?p=2595626)

This thread may be useful.  Its probably as simple as adding the line acpi=force to your /boot/grub/menu.lst

---

### Post by SirPerigrin on 2008-04-16
Thanks M8, that was all it took! Old hardware and new software just don't get along sometimes i guess.

---

