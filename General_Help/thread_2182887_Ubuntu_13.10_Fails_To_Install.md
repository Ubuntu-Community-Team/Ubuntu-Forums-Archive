---
title: "Ubuntu 13.10 Fails To Install"
date: 2013-10-22
forum: General Help
---

### Post by Vannyi on 2013-10-22
I've used Ubuntu for a few years now and have never had an issue installing new versions as they have been released.

With Ubuntu 13.10 now available, I thought it was time to upgrade.  I downloaded a copy, burnt it to a DVD and ran through the installation process.  There were no issues in Ubuntu seeing my hard drive in the computer and the build does complete.  Upon completion, it asks to reboot, the DVD auto-ejects and the PC reboots.

On the Lenovo T410 laptop, the laptop just hangs on a blank screen with the cursor flashing in the top left corner.
I've also tried to install it on a Lenovo ThinkCenter and in this case, I get the message "1962, no operating system found".

I've used a secure erase disk to fully wipe the drives and retried the install, but the same issue occurs.  I also did a full install rather then an upgrade from 13.04, same issue.

Any help would be greatly appreciated.

Thank you

---

### Post by Bashing-om on 2013-10-22
Vannyi; Hi ! Welcome to the forum.

Not knowing what graphics card you have this may be just a stab in the dark, but, surely worth trying:
Boot ubuntu, and as soon as the bios screen clears depress and hold the left shift key -> grub menu. With the top entry highlighted hit the "e" key for edit mode-> boot parameters screen-> arrow down and across to the term "quiet splash" and after this term insert "nomodeset" with out the quotes.
ctl+x to continue the boot process. Do you now boot to a GUI login ?
Enter your username and password -> desktop. 
Additional drivers: try the search term  "additional drivers" in the dash see if it brings up the utility and install the recommended driver.
(as I do not have 13.10 installed, nor do I use the standard desk top, I can not say where that utility is located)

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

