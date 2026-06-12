---
title: "Reverting to open source graphics drivers"
date: 2006-12-06
forum: General Help
---

### Post by Scheater5 on 2006-12-06
The proprietary ATI drivers aren't that great for my generation of Mobile cards - don't even support direct rendering, when the open source drivers do.  So I want to revert back to the open source drivers.  How do I do that?

---

### Post by annda on 2006-12-06
*disclaimer: this works on my ati mobility radeon 9700 on edgy. i don't see why you should have problems with it but maybe i don't know enough.*

this is what i did to revert from proprietary ati to opensource:

open synaptics and remove all fglrx stuff and maybe xserver-xgl (if you've installed it, i did for beryl but it wasn't reliable enough although i was led to believe that it would perform better).

edit you /etc/X11/xorg.conf file (back it up first!) and substitute fglrx with ati or radeon (in my case radeon is MUCH better).

alt+ctrl+backspace to kill/restart the Xserver and you are done.

---

### Post by Scheater5 on 2006-12-06
I've tried changing all occurences of fglrx to ati in Xorg, only to have X not start and have to copy the backup in the terminal.  Is there any way to change the driver via a graphical frontend maybe?

---

### Post by annda on 2006-12-06
i'm afraid that if you changed it manually to ati and it's still not working, some configuration options are not right (and no gui would help with that - i don't know of anything that would clean up the xorg.conf file).

run this:
```

sudo dpkg-reconfigure xserver-xorg
```

this will ask you some questions in textmode and overwrite the conf file (so keep your backup just in case).

good luck!

---

### Post by Scheater5 on 2006-12-06
Well, manually editing didn't do what I wanted it to, but I did figure out why X hadn't been starting (there was an instance of the letters "fglrx" in Xorg that didn't need to be changed).  It for some reason still wouldn't enable direct rendering.  I booted up the live cd - verified that direct rendering worked on it, and then copied xorg.conf to a usb disk and then rebooted and copied to it my hard drive - all to no avail.  So, I decided to to make another partition to "play" with and keep the existing one for work.  However, that's run into another problem in that Grub stopped recognizing the other partition.  Setting the "work" partition active and seeing if that works right now - will post the results here.  If it doesn't work, I'll probably make another thread for this new problem.

---

### Post by Scheater5 on 2006-12-06
No luck - loading up QTParted and changing the active partition to the first one (with the old setup on it) seems to be overwritten by a reboot.  The second partition automatically becomes active again.  Probably not working much more tonight - in the morning I'll make another thread for this problem - but if anyone who happens to be following this has any advice I'm gonna keep checking this one, too.

---

