---
title: "Startup Automation"
date: 2008-05-08
forum: General Help
---

### Post by Maconvert on 2008-05-08
Hello,

I’m currently working on a little project that will re-boot my old PC when the power comes back on after a failure (it happens about once every two months or so and it seems like I’m never home when it does).
The electronic end of it I have figured out.

The software end of it is another story.
I’ve got Ubuntu 7.10 installed on my machine.

First, I need my computer to automatically log in when the computer starts. I think I should be able to disable the login requirement though so that it isn’t even required, but I don’t know how.

Second, after booting into my PC, I need to mount all of my drives (about three of them) so that my software has access to them.

Third, I need to automatically launch programs (i.e. Deluge, Limewire, etc) and get past the annoying dialog boxes (i.e. “Do you want to upgrade to the latest version?” etc).

Can anybody tell me how to do these three things?

Possibly there is a root-level script that I can write.

Please let me know.

Cheers.

---

### Post by scragar on 2008-05-08
the autologin option can be adjusted from System>Administration>Login window

mounting your drives may be done using fstab, but I'd need more info on your drives to offer more help(or you could google fstab, the docs can be confusing though)

programs may be launched using System>Preferences>Sessions and adding startup programs, I'm not sure how to avoid any other notifications, wouldn't there be an option in program to turn them off?



EDIT: to get me your drive info, mount them as you are currently doing, then run ```
mount | grep media
```and paste output back here.

---

