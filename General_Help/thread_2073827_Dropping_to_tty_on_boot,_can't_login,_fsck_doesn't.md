---
title: "Dropping to tty on boot, can't login, fsck doesn't seem to help"
date: 2012-10-20
forum: General Help
---

### Post by Kasper Janssens on 2012-10-20
Hello,

I just had a power outage for a few seconds and my ubuntu desktop doesn't want to boot anymore, can't mount all the partitions so I'm guessing a problem on one of the disks. I tried to get into the grub menu and tried to get it boot like that, choosing resume as an option, after which a fsck operation started that found some errors and allegedly corrected them, after which it rebooted again.

Upon the next reboot, though, I didn't get to the ubuntu log in screen but dropped into tty, asking me to provide user and password. Everytime I try to log in, I get the message that my password or user isn't correct, which is weird. I cannot seem to get into the grub menu anymore, either, not by holding shift or so. I decided to try the live cd and run fsck like that, but that didn't report any errors anymore, and I still get the same issue, dropping into tty, not being able to log in.

Anybody an idea? Ubuntu 12.04 by the way.

Kasper

---

### Post by 2F4U on 2012-10-20
Do you have the correct keyboard layout in the tty? Could explain why it is reporting the wrong password (given that the password you enter is indeed the right one).

---

### Post by dniMretsaM on 2012-10-20
Boot into recovery mode and create a new user. Then reboot and try logging in as the user you just created. You could also check to make sure that your user didn't become locked somehow.

---

### Post by Kasper Janssens on 2012-10-20
Yes, I thought about the keyboard layout and such as well. That doesn't seem to be it. I also tried typing the password in the user field for that reason. I'm currently typing  this post on an ubuntu laptop, on which I have the same user/password combo and I can reproduce the problem here, type ctrl alt f1, try to log in and I get a login failure. But that's not the real issue I think, the problem is still that for one reason or another I can't get in the graphical shell. 

On that tty screen, when I press alt F7 to go back to the graphical shell, I get a complaint about a mount failed. The strange thing is that it's the nfs mount of my nas it complains about, hardly something I would think necessary to boot into X. I could maybe try to remove the mount statement of the nas from fstab through the live cd, but it feels like a sidetrack...

Kasper

---

