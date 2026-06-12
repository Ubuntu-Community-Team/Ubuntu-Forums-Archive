---
title: "Mouse Forward Button doing more than needed"
date: 2007-11-27
forum: General Help
---

### Post by noremac on 2007-11-27
I have a Logitech Revolution mouse and have succeeded in installing 'btnx' and getting all my wheels, scrolls, and various buttons to do what I want them to do. And exactly how I want them to...except for one. My forward button. I have it working both Firefox and explorer windows of Ubuntu, and it does what I want it to(going forward in views I was at that I had since gone back in...wow), but whenever I do click it, I also get an extra window but this one lets me Minimize, Unmaximize, resize and what not. Its the same window you get if you right click the title bar of a window, or right click a tab in your panel with the various windows you have open. I have the button programed to perform a Alt + Right Arrow combonation. If I manually do that in a Firefox, this extra Minimize etc window does not pop up of course. 

It seems as though there is another computer application, default perhaps, thats also riding on this button and performing another function causing this window to pop up. 

Any one know of what it might be cause its really annoying?
Thanks in advance,
Cameron

---

### Post by daou on 2007-11-28
It sounds like you are getting an extra right click, like most Revolution mice do with default Gutsy xorg.conf settings. You can try it by holding Alt and pressing the actual right button. It opens the menu you talk about.

Did you try changing your xorg.conf InputSection like described in the btnx manual's troubleshooting section? Set Protocol to "auto" and Device to "/dev/psaux" at least.

---

### Post by noremac on 2007-11-28
Excellent, thanks!
Wish I had done a little more research and seen that trouble shooter. Thanks a lot none the less! Appreciate the help.

-Cameron

---

