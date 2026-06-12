---
title: "Problems running 6.06 live cd - blank screen"
date: 2007-05-24
forum: General Help
---

### Post by Paul Sherman on 2007-05-24
Someone gave me a copy of 6.06 to try out, so I tried to boot it on my system
at work (they let me experiment a little).

It goes through the motions of booting up, shows various processes starting, etc.
Then the display goes blank, except for showing 'Unable to Display" and
Horizontal rate 81.4 Khz, Vertical rate 65 Hz.

I tried booting in 'Safe Graphics Mode' and 'VGA= 771' at boot for low res, no luck

It seems to boot fine (the Ubuntu start up jingle comes out of the speakers),
but no display.

Are there parameters I can pass at boot to try a default display (even
command line would be an improvement)? Can't install it if I can't see it...

The system under discussion uses a Viewsonics VG2000 LCD display and Intel
82865G video chip.   

In googling the combo of Ubuntu and Intell 82865g there seems to have been
issues.  Is this simply the the wrong version to try on this system?

---

### Post by adieb on 2007-05-24
of course you could try to use the newest vresion of ubuntu, 7.04 feisty fawn, just to try,,,

another thing is trying to change into another virtual terminal by pressing strg+alt+F1

then you should see typical linux console.

try to find out your monitors specs and fill  them into /etc/X11/xorg.conf

after that sudo /etc/init.d/gdm restart

---

### Post by Paul Sherman on 2007-05-24
> **adieb said:**
> of course you could try to use the newest vresion of ubuntu, 7.04 feisty fawn, just to try,,,

another thing is trying to change into another virtual terminal by pressing strg+alt+F1

then you should see typical linux console.

try to find out your monitors specs and fill  them into /etc/X11/xorg.conf

after that sudo /etc/init.d/gdm restart


Hmmm....

This the latest version I have, can't download another (at home, bandwidth is awful,
and no CD burner).  But I do have an older distro I can try here (it's installed on my
home system)

Can I write to a file while running the live CD? 
Does it just store those changes in RAM?

---

### Post by Paul Sherman on 2007-05-24
Thanks for the commands for getting to the command line.

The CD was definitely up and running, but no graphical display.

Back to the earlier question; are configurations stored someplace while
running off the live CD (RAM, virtual swap on hard drive, ???).

---

### Post by wpshooter on 2007-05-24
May I ask if you ran an integrity check on the Ubuntu Cd by running the verification function that is found on the initial boot screen menu ?

---

### Post by Paul Sherman on 2007-05-24
I have not, thanks for the suggestion, will do so when I get a chance
to try it again.

---

### Post by wpshooter on 2007-05-24
> **Paul Sherman said:**
> I have not, thanks for the suggestion, will do so when I get a chance
to try it again.

Not Paul Sherman of Bedford, Va. by any chance ???

---

### Post by Paul Sherman on 2007-05-24
Sorry, I live in St. Louis, dislocated Oregonion

---

