---
title: "GRUB help"
date: 2008-07-04
forum: General Help
---

### Post by Shaided on 2008-07-04
I put in my bootable XP disc GRUB comes up says press any button to boot from disc I press a whole bunch of buttons and nothing happens.:(

---

### Post by Gunman1982 on 2008-07-04
That is not grub, that is your bios boot. Did you try to push enter? And give it some time, check if the cd-rom starts to blink like crazy. Maybe the disc is damaged.

---

### Post by Shaided on 2008-07-15
Bump
~help please
I've tried pressing Enter it doesn't respond when I press anything and it just starts up Ubuntu.
What is my bios boot what do I have to do to fix it....?

---

### Post by sandysandy on 2008-07-15
what is the boot sequence.

also have u tried the XP disc on any other computer to check its OK.

regards

---

### Post by Shaided on 2008-07-15
The CD works perfectly I've used it to make virtual machines..

---

### Post by jimv on 2008-07-15
Is this a USB keyboard?

---

### Post by Shaided on 2008-07-15
the keyboard isn't USB '-_-

---

### Post by WRDN on 2008-07-15
In your BIOS, look for the "First Boot Device" option. Change it to CD/DVD Drive, or something similar. Also, you may wish to change the Second Boot Device to the Hard Disk Drive, so if it doesn't find the disk, it will boot from the HDD. Now save the changes, and the PC will reboot. It should now boot the CD.

---

### Post by jimv on 2008-07-15
Well that's odd.  For some reason the loader for the XP disk isn't recognizing your keyboard strokes.

Here's a crazy idea.  As soon as your computer comes on and you see the bios screen, start tapping your spacebar like crazy until the "Press any key to load setup" screen comes up.

---

### Post by Shaided on 2008-07-15
> **WRDN said:**
> In your BIOS, look for the "First Boot Device" option. Change it to CD/DVD Drive, or something similar. Also, you may wish to change the Second Boot Device to the Hard Disk Drive, so if it doesn't find the disk, it will boot from the HDD. Now save the changes, and the PC will reboot. It should now boot the CD.

Okay where is my BIOS...?

---

### Post by Shaided on 2008-07-15
> **jimv said:**
> Well that's odd.  For some reason the loader for the XP disk isn't recognizing your keyboard strokes.

Here's a crazy idea.  As soon as your computer comes on and you see the bios screen, start tapping your spacebar like crazy until the "Press any key to load setup" screen comes up.Try to post something usefull next time...

---

### Post by jimv on 2008-07-15
Actually, I searched for similar issues for half an hour, and the only "solution" I found was a guy who said that if he pressed a button on the keyboard repeatedly until that screen came up, he was *sometimes* able to get it to load.

Try not being rude to people trying to help you next time...

EDIT

Also, don't have an attitude when you bring yourself and your ignorance to the forum to get help.  You obviously are a novice computer user (do not know how to get into the BIOS), and shouldn't be calling more experienced users' suggestions useless.

Here's your situation right now.

The computer is trying to boot from the CD.  You don't need to change anything.  The "Press any key to boot from CD" message **IS THE XP CD**.  If you see that message, then your computer is already booting from the XP cd, and the XP cd wants to know if you wish to continue.  At this point, it is really **no longer an Ubuntu issue** and you should be checking with a Windows forum.

Since I'm a nice guy, I'm going to tell you your options.  You're using a PS2 keyboard, so there isn't anything in the BIOS that is going the help you.  You can either try a different PS2 keyboard, or try to use a USB keyboard.  Of course, you might not know that you're using a USB keyboard, so check...it makes a difference.  USB looks like this:

[http://blogs.s60.com/s60multimedia/usb%20002.jpg](http://blogs.s60.com/s60multimedia/usb%20002.jpg)

Sorry if that insults your intelligence, but you've insulted me.

---

