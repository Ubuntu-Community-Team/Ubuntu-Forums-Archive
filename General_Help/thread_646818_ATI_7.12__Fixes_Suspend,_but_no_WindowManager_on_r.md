---
title: "ATI 7.12 : Fixes Suspend, but no WindowManager on resume"
date: 2007-12-21
forum: General Help
---

### Post by fictivetoast on 2007-12-21
ATI Released new fglrx drivers yesterday (7.12) which FINALLY allow me to suspend and hibernate on my Mobility Radeon x2300 with the standard Ubuntu SLUB kernal!  Hooray!

I have a problem though : whenever I resume, everything comes up fine except for Beryl.  So my windows are all without borders, and anything drawn by gnome has a fat white border around it (ex panels, tooltips, file menus, etc).

I can fix this by opening a terminal and typing:  sudo emerald --replace
BUT if I do this, I have to leave the terminal open indefinitely, since closing it would close emerald returning me to the same problem with which I started.

Anybody have any ideas as to what I can do to work around this?  Is it possible to make a really simple bash script to be executed upon resume that would restart emerald without my needing to manually open a terminal?  Or better yet, does anybody have any idea why emerald wouldn't be coming up in the first place?

Thanks in advance!

---

### Post by fictivetoast on 2007-12-22
Bump?

---

### Post by insert_name_here on 2007-12-30
Go into /etc/acpi/resume.d/

Then make a script to execute emerald --replace.  I'm not sure where to put it the order of the scripts there (they are numbered, e.g. 65-console.sh), so play around with it and report back.

Does it suspend correctly everytime?  My laptop seems to have issues with suspend, even with 7.12.

---

### Post by WaySensei on 2007-12-30
My Macbook Pro with ATI Radeon X1600 running Gutsy still can't suspend with 7.12 as well...

---

### Post by fictivetoast on 2008-01-11
As far as the suspension goes, everything else is working wonderfully - sound comes up instantaneously (if a track was playing in rhythmbox upon suspend, it picks up right where it left off), and networking kicks back in after a few moments.  Not sure if it'd make any difference, but I installed the 7.12 driver manually using AMD's installer script, instead of by generating seperate deb packages for it ; for whatever reason, this seemed to work better for my suspending ability than the standard package route.
--------------------------------------------------

Hmm...  I've tried throwing a script into the resume directory (stating simply that it be bash, then "emerald --replace"), and I've made it executable, but so far don't seem to have had any luck with it.  I've tried mostly upper level numberings (89, 99, etc).

I think the issue is that the "emerald --replace" command needs to come AFTER I unlock my screen.  So does anyone know how to either
a) Get the script to run on the user level upon the screensaver's unlocking the screen?
OR
*b) MORE PREFERABLY - how to prevent the screen from being locked in the first place?  I really would rather not have to retype my password every time I open the laptop lid...*

Any help on either of these would be greatly appreciated!

---

