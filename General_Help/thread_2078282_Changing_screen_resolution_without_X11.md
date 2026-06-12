---
title: "Changing screen resolution without X11"
date: 2012-10-30
forum: General Help
---

### Post by a-dougk1 on 2012-10-30
I am attempting to set up some file servers using Ubuntu 12.04 with Samba. I have an old LCD monitor set up as a display. When I finish installing Ubuntu, after the first reboot, the monitor crashes because it cannot display the resolution used by Ubuntu.

I am only using a command line, that is, I haven't installed X11 because it isn't necessary. I would assume that, in this case, the default resolution would be 640x480 @ 60Hz. Apparently, it is not.

So, is there a way to change the resolution that Ubuntu is trying to display in a command line only system?

Thanks,

Doug

---

### Post by ajgreeny on 2012-10-30
I've never needed or used it but here's a possibility.
[https://help.ubuntu.com/community/ConsoleFramebuffer](https://help.ubuntu.com/community/ConsoleFramebuffer)

---

### Post by a-dougk1 on 2012-10-30
The instructions at that location are apparently out of date since there is no menu.lst file (or any other *.lst file) that contains any of the information having to do with VESA resolution settings. If they've been moved, I haven't been able to find them.

Thanks anyway.

Anyone else have any ideas?

---

### Post by ajgreeny on 2012-10-30
Try adding the resolution you want into the /etc/default/grub file in the line ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet vga=791"
``` or whatever is your wanted resolution as shown in that link?

That will do exactly the same as you could in the past by editing menu.lst and adding it there.

EDIT:
Another quick search has thrown up this thread which may be the correct answer.
[http://ubuntuforums.org/showthread.php?t=1909337](http://ubuntuforums.org/showthread.php?t=1909337)

Sorry if I misled you before. The subject is something I did not think about too much before, but was intrigued enough to look into.

---

