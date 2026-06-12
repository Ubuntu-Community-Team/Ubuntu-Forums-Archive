---
title: "'Time stamp too far in the future'...with an exciting new twist!"
date: 2008-02-28
forum: General Help
---

### Post by BetterSense on 2008-02-28
I've been bouncing all over the forums recently trying to get a straight answer on why I can't enter administrator mode in the KDE gui, or even open synaptic, set my clock, install languages, change group permissions, or anything that requires a password (it sometimes prompts for a password and then just does a windows). 

 I came up with a bug report from 2005 for this exact problem, not being able to do anything requiring admin privileges from the gui, which I was able to 'solve' by using sudo kcontrol which opens up a different dialog with (it would appear) all the options available through KDE...I can only change any of the administrative stuff by running sudo kcontrol...not just kcontrol. If I just run Kcontrol it has its own administrator mode bit, which doesn't work in exactly the same way,but apparently sudo kcontrol works. 

Well the first thing I did is adjust my date and time. YAY, my clock works, right? 

Well now I get a 
[PHP]
sudo: timestamp too far in the future: Feb 27 19:22:45 2008[/PHP]

So back to Ubuntu forums I go! Fixes I've found on the forum involve 

1. Setting your clock back, and going forward in 15 minute increments--but wait, I can't adjust my clock without sudo!

2. Running sudo -v which lets you reset your timestamp--But sudo doesn't work! I get the same error. 

Other suggestions include resetting your clock back to the time stamp shown in the error, THEN running sudo -k, sudo -K or sudo -v,......but ,,,wait for it....

I CANT ADJUST MY CLOCK WITHOUT SUDO BECAUSE OF THE ADMINISTRATOR MODE BUG, AND I CANT USE SUDO BECAUSE I CANT ADJUST MY CLOCK!!

Isn't that great? The only way I can adjust my clock is with sudo kcontrol! 

I'm almost as amused as furiated. It reminds me of when I rode my blue chocobo across the FFVII world map and accidently released it, leaving me no way to get back to my airship.

---

### Post by pointone on 2008-02-28
Try rebooting in recovery mode and setting the clock there.

---

