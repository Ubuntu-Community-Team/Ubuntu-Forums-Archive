---
title: "Erratic mouse cursor behavior"
date: 2016-12-08
forum: General Help
---

### Post by And1945 on 2016-12-08
Hi,

I was wonderig if some of you have had issues with the mouse cursor jumping to the top right corner of the screen, jumping around and clicking the left mouse button. The mouse is not to blame, since this now has happened on my dads computer as well.

For stability reasons I have put him on 16.04 LTS.

Also, I have followed these instructions: [http://askubuntu.com/questions/504531/mouse-snapping-back-to-upper-right-hand-corner](http://askubuntu.com/questions/504531/mouse-snapping-back-to-upper-right-hand-corner)

I should mention that both computers this affected has been stationary computers. One Lenovo an one HP Microserver. Other mice has been tested, and same issue occurs. The error has not been noted on Fedora, only on Ubuntu based installations. I do not beleive it has to do with Mate.

I appreaciate any input.

---

### Post by And1945 on 2017-02-02
*Bump*

So far, I seem to have narrowed it down to either the bundled Synaptics driver or X11 causing this behavior. Another theory could be the input locale da-dk being at fault, since both affected computers, both had Danish keyboards plugged in. The issue does happen in Anaconda installers before selecting the danish keyboard outlay.

I am at my whits end here.

---

### Post by Bucky Ball on 2017-02-02
You have 16.04 on your dad's computer and no issues? What do you have on your computer that is causing issues and does 16.04 run okay with no mouse issues on your computer?

Your dad's computer is better off with an LTS release anyway unless he, or probably you, feels like upgrading it every six months. Up to you with your own I guess.

---

