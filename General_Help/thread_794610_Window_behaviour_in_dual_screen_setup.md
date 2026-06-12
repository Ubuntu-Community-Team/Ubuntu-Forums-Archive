---
title: "Window behaviour in dual screen setup"
date: 2008-05-14
forum: General Help
---

### Post by keforex on 2008-05-14
I have two 30" screens running at 2560x1600 each, giving me a desktop that is 5120x1600. They are fed by a nVidia 8600.

Everything is working fine, except that any windows that are open by other applications are always in the middle of the big desktop, so half of the window is on the left screen, half on the right.

What I need is to have those windows to open on either left or right. I am running 8.04 and when I had 7.10 it did work as I wanted. Not anymore. Also, the top panel that has the main Ubuntu menu now extends all the way to the right screen, while before it was only on the left screen.

I am using compiz and the X interface selected as of now is "X Script". If I choose any other X session, the dual screens get all messed up.

So basically what I need is to have a "non extended" desktop when it comes to panels but still be able to move the mouse cursor between the screens at will, as well as move windows around both screens.

Any suggestions?

---

### Post by rune0077 on 2008-05-15
Hey

Do you have nvidia-settings installed? If not, you should install it. Then from application > system tools > nvidia settings, go to the display config, click the screen you want your windows to open in, and mark the box that says something like "use this as primary screen". That should do it.

I also had the panel issue, but it fixed itself after I did a reboot.

---

### Post by keforex on 2008-05-15
Yes, it's installed but it doesn't work. It tells me I have to run nvidia-xconfig as root, which I already did, but the problem persists. In fact, now my other screen isn't working anymnore, I created another thread with this problem so I'd rather keep the replies there and not here. Here's the link: [http://ubuntuforums.org/showthread.php?t=794689](http://ubuntuforums.org/showthread.php?t=794689)

---

