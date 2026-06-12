---
title: "Screen Res different to Xorg.conf - why?"
date: 2006-10-17
forum: General Help
---

### Post by Tamed_G on 2006-10-17
](*,)  Hi all,

I have my Ati x800XL installed using fglrx with the 8.29.6 drivers showing everything is fine in fglrxinfo and clocking 7000+ fps in GLXgears.

Trouble is the screen resolutions option in Gnome seems to bare no resemblance to the resolution specs in my xorg.conf file.

Can anyone point out what would cause this? 

Thanks

G

---

### Post by CatKiller on 2006-10-17
My understanding is that the card's BIOS will report to X the resolutions that it can do as VESA modes. X will add to this list those resolutions that are included in xorg.conf. X will then try the highest resolution in the list, and if it can't do it, because of monitor refresh rates or memory usage or whatever, it will remove that resolution from the list and attempt the next one.

Hope this helps.

---

### Post by PrinceArithon on 2006-10-17
I Know what your problem is.  It's the same problem I have had.

What you want to do is shut down your xwindows session go into shell, open up the xserver and go in and configure it.  Here is a kinda step by step

In your terminal type in:

sudo /etc/init.d/gdm stop


This will stop the GUI and put you into the shell, you may have to log in again...I forgot if you have to or not.  Anyway after you are all set in the shell type in

sudo dpkg-reconfigure xserver-xorg

What this will do is take you to a kinda setup wizard for Linux.

Anyway go through all the defaults of the wizard until you get to the part where it shows your resolutions.  To go through the resolutions hit the up or down arrow key, to select resolutions use the space key.  After you are done hit enter and keep going through the defaults of the setup.  When you get back to the shell type in

startx or sudo startx and you will start up in the GUI with the highest resolution available to you.

I hope that helps

Aaron

---

