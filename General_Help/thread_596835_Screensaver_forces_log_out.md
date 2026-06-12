---
title: "Screensaver forces log out"
date: 2007-10-30
forum: General Help
---

### Post by deusxechelon on 2007-10-30
When the screensaver comes on or I go to the screensaver panel, it logs me out and puts me at the ubuntu log in screen. I changed a few things attempting to make AWN and compiz function, neither attempts were successful. Not sure how any of them relate to the screen saver. Any ideas?

---

### Post by dayvy on 2007-10-30
Does it actually kick you out to GDM or does it just lock your screen? There is an option to lock the screen when the screensaver comes on.

d.

---

### Post by deusxechelon on 2007-10-30
It logs me out to the login screen. The option you speak to lock screen is not selected, I have about 10 seconds to adjust the screensaver time (Which I managed to scroll up to 1 hour 1 minute) or check those boxes before it logs me out. Something is wrong with the rendering of the screensavers, when the preview loads, i get logged out.

---

### Post by misfitpierce on 2007-10-30
Yes I noticed this recently on Gutsy 64 bit. Did not do it upon fresh install but after some updates it did it. Does not bother me much as I use Floating Ubuntu which is not affected by this but feisty 64 bit also did this lol.

---

### Post by LeTenken on 2007-11-10
i have this same problem.

I get logged out on some screensavers, probably the ones with 3d acceleration.  Under the screensaver window i can preview the 3d-accerated screensaver just fine, but if i press the "preview" button i get logged out immediatly.
I use the fglrx driver on the Radeon x200 Mobility (the computer is on a laptop).  I was able to get Compiz to run fine and according to glxgears, my 3d acceleration should be ok too.
Anyone have any ideas?  Anything else i should be posting to clarify?  This problem is also probably connected to some of the other problems i am having with other 3d-accelerated programs.  Where if i enable compiz some of my applications will log me out of X if i try to run them.  And its annoying to always disable compiz to run these apps.

---

### Post by shaynegryn on 2007-11-13
Hi had the same problem on Gutsy. Previews of screensavers work fine, but as soon as one kicks in for real, it kicks me out to the login screen. My solution was to enable "Lock screen when screensaver is active". For some reason, although it would lock the screen as indicated, would not actually log me out of my session.

---

