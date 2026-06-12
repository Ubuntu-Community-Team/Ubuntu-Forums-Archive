---
title: "CD/DVD ROM cannot &quot;mount&quot;"
date: 2008-04-03
forum: General Help
---

### Post by DMBoricua on 2008-04-03
I may know the problem, but im not sure if this is the cause.

I did change my CD/DVD ROMs because we had an older computer case in a closet in our house and it so happens that it had 2 drives that were better than the ones I had, so I switched them. When I had the previous CD ROMs I never had a problem. Its been a couple of weeks ago that I switched the drives.

Today I booted up to Ubuntu and I wanted to play Starcraft (using Wine ofcourse) and I would just put the CD in, open starcraft with Wine and it would read the disc and I am able to play. When it doesnt detect the disc it tells you the normal error that it doesnt find the disc. I do have the disc in, but I get "Cannot mount volume. Invalid mount option when attempting to mount the volume 'BROODWAR'" now :-? Anyone know how I can get the new drives working?

---

### Post by fsmithred on 2008-04-04
Couple of thoughts on that - 

Make sure the jumpers on tha backs of the drives are set properly and you know which device is which (hdc, hdd?). Check the cable connections while you're in there. Make sure the device name matches the name used in /etc/fstab.

Try the CD on another computer and see if it reads. Try a different CD on this computer.

What mount options did you try? Try to figure out which option is invalid. Try mounting it from command line if you haven't already tried that. (something like, 'sudo mount /dev/hdc /media/cdrom')

---

