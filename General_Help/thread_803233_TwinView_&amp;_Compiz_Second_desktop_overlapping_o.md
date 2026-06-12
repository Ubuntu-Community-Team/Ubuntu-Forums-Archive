---
title: "TwinView &amp; Compiz: Second desktop overlapping on cube"
date: 2008-05-22
forum: General Help
---

### Post by UnixGeeK on 2008-05-22
Hey, having one annoying little problem with compiz.

[ATTACH]71097[/ATTACH]

As you can see, when I use the cube or zoom for example, I see the tv monitor overlay from second monitor.

Here are the 2 screens from nvidia-settings:

[ATTACH]71098[/ATTACH][ATTACH]71099[/ATTACH]

Really not sure how to fix that, as I've tried many different settings in the nvidia program. Though the displays on each monitor are fine, I get this "clone" on my main screen whenever I use these compiz effects.

One workaround is to use separate xservers (2 separate screens), but then I get this known bug where menus and popups are getting slow. So anyone seen this problem before and know how I can get it fixed?

Thanks in advance. :)

---

### Post by rune0077 on 2008-05-22
You can see the issue on the second screenshot of your nvidia-settings: the two monitors are placed on top of each other, when they should be next to one another instead. Just click the screen you want to move, then from the "Position" drop-down menu select "Right of", this should position the screen to the right of the other one (alternatively you could just drag it to where you want it on the layout-screen). Remember to click "Apply" once you have it set.

---

### Post by UnixGeeK on 2008-05-22
Well the thing is, if I do that, the whole display becomes somehow stretched across both screens, and that's not what I want.

I tried to choose "clone" also, but nothing happens when I apply and save. (Yes I use sudo command to start the program) ;)

---

### Post by rune0077 on 2008-05-22
> **UnixGeeK said:**
> Well the things is, if I do that, the whole display becomes somehow stretched across both screens, and that's not what I want.

Well, that's pretty much what TwinView is supposed to do (i.e. have your whole desktop stretched out over two screen). If you want to have seperate desktops on each screen, you'll have to go with the "seperate x-screen" thingy instead.

---

### Post by UnixGeeK on 2008-05-22
Hmm well then I guess I have to do that. Can't use compiz though, because of the lag of opening menus and resize windows. Hopefully they fix the issue eventually.

Anyway, thanks for the help so far :)

---

