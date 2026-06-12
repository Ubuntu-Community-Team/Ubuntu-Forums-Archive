---
title: "Gutsy Install buggered, wont boot"
date: 2008-01-31
forum: General Help
---

### Post by pyriX on 2008-01-31
Hi guys.

I've been using ubuntu for about 6months now, and have overall been happy with it until now, and even then im not sure it's ubuntu's fault.

To dive straight into the problem -> My system was refusing to work properly with the side panel on (given I live in australia and we're alternating between 15 and 30 degree heat, and the humidity is all over the place, not surprising, especially not with two other computers, 3 screens and a projector in my small room, as well as miscellaneous other computing gunk. The point im getting at here is that it was overheating, the stock intel cooler just wasn't cutting it. But given im strapped for cash at the moment, I just left the side panel off and everything was getting along dandy. But today, this afternoon in fact, the system locked up again with the panel off (and it was a cool day), so i rebooted. It got past the sexy ubuntu flash screen, then brought up a full screen terminal. Said that the install disk was rooted essentially, and it was going to check it for errors. It did so, found some and did nothing. Successive reboots produced the same result.

Essentially what I'm after here is a) What the bleeding heck is the problem.
B) Can I fix the problem without doing a clean install (anything akin to the repair installs of Windblows?)
C) Failing to fix without a clean install, can i retrieve my documents which when i boot to the live install cd refuse to copy becuase i have inadequate permissions in both GUI and command line?

Any and all help would be greatly appreciated. If you need more details, im pretty sure I wont have any trouble reproducing the problem ^o)

---

### Post by jken146 on 2008-01-31
A)  If this is **fsck** that you are referrring to, just let it run.  It may take quite a while.

B)  There is no 'repair install' like in windows, but if it is a filesystem problem, you may need to recreate the filesystem in question.  See if you can get fsck to finish first.

C)  When using the live CD, use sudo or gksudo to get root permissions.  For example, to use the file manager as the super user, press Alt+F2 then type **gksudo nautilus**

---

### Post by ajgreeny on 2008-01-31
You can also try running fsck on the ubuntu installation partition from the ubuntu liveCD.  I really don't know why it should happen, but sometimes fsck will run from that whereas it will not finish properly running at bootup time.  Anby file system you run fsck on must be unmounted so make sure of that before you start the process.

If your ubuntu install is on hda2, as it often is in the case of a dual boot system, the command from the liveCD terminal would be ```
sudo fsck /dev/hda2
``` (can't remember if it needs sudo, so try both to find out)

You can use other options with the command eg -V to give a verbose output of the process, but it's not really needed, so try first without and see if it gets to the end successfully.

---

