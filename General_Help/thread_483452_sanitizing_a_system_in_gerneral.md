---
title: "sanitizing a system in gerneral"
date: 2007-06-24
forum: General Help
---

### Post by BobLand on 2007-06-24
I began using feisty in mid April.  I struggled for a long time to get the system to recognize my video card.  Eventually, after many attempts I found the resolution I was looking for but not after doing numerous installs.

My crt monitor died.  At first I thought it was the video card so I bought a new one - nvidia 7300.  After having so many problems initializing video I decided to try the card with W2K since it was a known environment.  Still no video.  Then I bought a Samsung 226BW.  WOW! Sharp as a tack, gorgeous colors, no dead/stuck pixels.  Now that I got that solved I went back to Ubuntu and tried the same thing.  

The video card, obviously, did not have a linux driver but I found one at the nvidia site.   Unfortunately, it would not display the 1680x1050 optimum resolution for the monitor.  

I began fooling around with xorg.conf until it broke beyond repair.  Used an original backup but it didn't work.

Searched thru the forums for clues.  Tried a few but none worked.  Felt the only thing left was to back up what I could and reinstall.

With a spanking new install I decided to proceed cautiously.  Found a number of posts that suggested to install from synaptic.  Got it on the second attempt.

My worry is, trying to get Evolution/Jpilot/KdePim..etc to work, I'm going to have to do a lot of installing and removing.

Is there a way to ensure that I don't leave garbage behind when I remove packages or otherwise keep the system clean from junk?

Thanks,
bobland

---

### Post by jpeddicord on 2007-06-25
If you think there are extraneous packages and files on your system, just run the following in a terminal.
```
sudo apt-get autoremove
```
It will look for any packages that were installed automatically (usually along with other packages), and remove them.

Jacob

---

