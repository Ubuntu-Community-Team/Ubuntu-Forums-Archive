---
title: "Cannot resize Firefox"
date: 2007-05-22
forum: General Help
---

### Post by n8wood on 2007-05-22
The top and bottom borders of Firefox seem to be locked in position, snug up against the gnome toolbars. I can resize horizontally, just not vertically. It's pretty annoying when I'm trying to take screenshots and minimize the image size. I tried rebooting and using the Alt+F8 resize hotkey, neither helped. 

Any ideas?

---

### Post by n8wood on 2007-05-23
bump...

---

### Post by AlwaysLearning on 2007-06-23
I have had the same problem on Feisty Fawn ever since the upgrade to FF 2.0.0.4 was pushed out.

All of my other Gnome apps can resize their windows normally in both the vertical and horizontal directions, but FF's top- and bottom-borders are stuck to the edges of the visible desktop area. Resizing only works on the left- and right-borders using either the mouse or keyboard (Alt+F8 ) and the Resize tool in the Web Developer plug-in also only affects the width of the window.

I'm not using Beryl or Compiz, either, just the out-of-the-box unaccelerated drivers with Metacity.

---

### Post by wjp.reg on 2007-06-23
Same here.

I had a similar experience trying to log on to the keyring manager at start-up.  The keyring password prompt window gets minimized and the only way to raise it is to right-click on the bar and choose ¨On Top¨

Maybe there is more to this than meets the eye and perhaps it is not limited to firefox?

---

### Post by GandalfTheNerd on 2007-06-27
I have the firefox full-height problem too.  I have been fiddling with the display resolution, and wonder whether this has some bearing on the problem.  Now, if I change the vertical display resolution, firefox automatically resizes to match the display height.

I'm still pretty new to Linux, but continue to be impressed with the Ubuntu system generally.  This is the first time I've found a hitch with the basic tools.

---

### Post by wjp.reg on 2007-06-27
> **wjp.reg said:**
> Same here.

I had a similar experience trying to log on to the keyring manager at start-up.  The keyring password prompt window gets minimized and the only way to raise it is to right-click on the bar and choose ¨On Top¨

Maybe there is more to this than meets the eye and perhaps it is not limited to firefox?

My problem was solved after disabling the desktop effects properly.  You need to only press the 'enable' button once ;-)

Now my windows work properly.

---

### Post by phlospher on 2007-06-29
try getting rid of your localstore.rdf file in your .mozilla/firefox/XXX.default directory. The directory I named "XXXX" here is some random sequence of characters.

This worked for me.

Phil

---

### Post by eladamri on 2007-07-01
> **phlospher said:**
> try getting rid of your localstore.rdf file in your .mozilla/firefox/XXX.default directory. The directory I named "XXXX" here is some random sequence of characters.

This worked for me.

Phil

Thank you. This solved the problem for me, but I wish there was a solution rather than a work-around.

---

### Post by jekewa on 2007-09-27
It also works to maximize and restore Firefox (so it fills the screen and then goes back to the size it was). Somehow this releases the "hooks" the frame seems to have to the top and bottom panels.

Doing this for one FF I had open seemed to release the bond for other open windows, too.

Just in case someone's keeping score, I have not had the experience with any other program, although I do have many programs that I'll extend completely in just one dimension (wide terminals, tall e-mails, etc).

---

### Post by Shiva88 on 2007-10-09
> **phlospher said:**
> try getting rid of your localstore.rdf file in your .mozilla/firefox/XXX.default directory. The directory I named "XXXX" here is some random sequence of characters.

This worked for me.

Phil

This also did the trick for me!  Thanks for the tip.

Also... maximizing and resizing did *not* fix the problem for me, so for anyone else who has this problem... definitely look into deleting localstore.rdf!

---

