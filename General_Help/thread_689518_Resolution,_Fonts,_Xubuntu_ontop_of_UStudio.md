---
title: "Resolution, Fonts, Xubuntu ontop of UStudio"
date: 2008-02-06
forum: General Help
---

### Post by treehuggerguy on 2008-02-06
I'm having some strange issues with a Toshiba Satellite laptop.  Based on its specs it should be able to run Ubuntu (though it has barely enough memory).  I did manage to get a system up and running by using an Ubuntu Studio disk.  It's had a ton of problems, though and I'm having a hard time figuring out how to troubleshoot them and some of them are not consistent.

1st, the resolution that it seems to default to is really ugly (700x600ish).  I was able to switch to a resolution of 1152x864. but I gdm will not change.  Hitting the icon to configure the login window crashes the machine.

2nd, sometimes upon logging into gnome the system will not start the background or icons and I am left with a black background.

3rd, I installed the xubuntu package (gnome is running pretty slow on this machine).  All of the fonts are gigantic and can't be managed with xfce.  By gigantic, I mean about 20-30 pt.  This is standard throughout xfce menus and applications.

Since I'd really like to get this working with xfce, I tried booting from an xubuntu disk, but that started with the ugly resolution and wouldn't display the menu bars even after correcting it.  Thus, I'm guessing I would have the same issues with a reinstall.

I had been running elive, but it became suddenly unstable and I decided to try installing ubuntu again.

Thanks for whatever help you can offer.

---

### Post by treehuggerguy on 2008-02-07
An update:

I've managed to install Xubuntu from the CD.  Apparently part of the issue is that the laptop screen is dead, so I've been plugging it into a separate monitor.  I didn't realize this would cause so many conflicts.  The only way I was able to boot the Xubuntu cd without it getting really ugly was to unplug the monitor and boot as if it were running on the LCD screen (which doesn't display anything).  After that, I could plug in the monitor and get it to work as if it were displaying a mirror image of the laptop lcd.

It seems to cause other problems though.  I've tried just about everything to get direct rendering to work, with no dice.  For a while it showed that I was running VESA.  I've now got that changed to Intel 810.  I suppose I should start a new thread for this issue.

---

