---
title: "ubuntu logo funky psychedelic colors on shutdown"
date: 2008-05-14
forum: General Help
---

### Post by yochaigal on 2008-05-14
Ever since I installed Hardy Heron (clean install) I've been having this problem at shutdown: the logo/splash image is funky with colors. Obviously I can't take a screenshot of this, and I don't have a camera. but you get the idea.  
I have an Nvidia 7600 GS graphics card (AGP).
I have removed and reinstalled the usplash image, to no avail.
This problem exists on launchpad but there isn't any fix posted.

See lspci below.

Any Ideas? 

Thanks

---

### Post by halogentan on 2008-05-16
sudo gedit menu.lst

remove "vga=791" from defoptions.  It should probably look like this:
# defoptions=quiet splash

Save it.  Close it.

then run the following command:
sudo update-grub

That should fix it.

---

### Post by yochaigal on 2008-05-16
defoptions is already remarked out... what would removing it do?

it looks like this right now:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=775

?

thanks

---

### Post by halogentan on 2008-05-16
remove "vga=775" from defoptions.  leave the rest of defoptions alone.

Then run:
sudo update-grub

Like I said, that should fix it.

---

### Post by yochaigal on 2008-05-17
Okay, that kinda works.

Now, I get a black screen with very large text.  Usually I get a few messages, involving network manager shutting down.
This time, it was 5 times the size, and then switched to the correct splash screen, but with only two or three seconds left in the progress bar.

Thanks though!

---

### Post by halogentan on 2008-05-17
Try installing StartUp-Manager.  Just make sure you backup /boot/grub/menu.lst first.  I know it's for the startup, but it effects the shutdown screen as well.  I think there's an option for "show text during boot".  You could try unchecking that.

Sorry you're having such problems.  I had the same problem last night and that fixed it right away.

---

### Post by yochaigal on 2008-05-17
Yeah I've been using SUM for a while, that's what i removed usplash with.... i'll play around.
thanks!

---

### Post by bcschmerker on 2009-04-21
> **halogentan said:**
> Try installing StartUp-Manager.  Just make sure you backup /boot/grub/menu.lst first.  I know it's for the startup, but it effects the shutdown screen as well.  I think there's an option for "show text during boot".  You could try unchecking that....I have a variation of the initial problem this Thread, with both "Show boot splash" and "Show text during boot" engaged:  The Startup checklist displays normally below the "ubuntu" Usplash and progressbar; but during the Shutdown sequence, the X server stops and I get a screen with a flashing cursor and no checklist when I expect to see the shutdown checklist.  Any clue what gives here, and whether a manual edit of a file in /boot/grub (if so, which one, please!) is needed?

---

