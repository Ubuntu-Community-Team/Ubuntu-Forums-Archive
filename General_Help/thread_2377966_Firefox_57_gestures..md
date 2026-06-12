---
title: "Firefox 57 gestures."
date: 2017-11-18
forum: General Help
---

### Post by leunam12 on 2017-11-18
Well, the dreaded Firefox 57 has arrived and most of my extensions are gone, well, that is life, can't stay in the past forever, have to move on with the times. 
The issue that I am having right now is that I finally found a gestures extension that works with this new version of Firefox, but every time I use it, the right-click menu pops up. 
This doesn't happen in Windows, only in Ubuntu.
Right now I am using Foxy Gestures since the recommended (Gesturefy) does not work in Ubuntu at all.
foxy gestures works but it doesn't work on the home page (FF's default) and where it works it always brings the right-click menu pop-up.
So, the obvious question is: is there a way to fix this?. Thanks.

How to duplicate the problem:
1-Install Firefox 57
2- Install Gesturefy or Foxy gestures
3- Try to use any gesture such as dragging with the mouse's right button to the left (history back).

Expected result: A line is drawn on the screen following the mouse movement and the action linked to the gesture will execute, a pop-up menu does not appear.
What I am seeing now:
   -Gesturefy: Only the Right-click menu pops-up. No trail is seen and the action is not executed.
   -Foxy Gestures: The purple trail is seen and the action executes but also the pop-up menu appears.

Again this does not happen in Windows.
Thank you again for any help.

---

### Post by Kelner on 2017-11-18
Sadly, this is an issue with Firefox itself (Windows builds treat right-click differently from Linux and macOS), one that cannot be worked around by extensions: [https://bugzilla.mozilla.org/show_bug.cgi?id=1360278](https://bugzilla.mozilla.org/show_bug.cgi?id=1360278)

---

### Post by Holger_Gehrke on 2017-11-18
The authors of both extensions know about the problem and warn about it on the extensions page.  The workaround both offer is to use another mouse button.

Holger

---

### Post by leunam12 on 2017-11-18
Ok, I'll check the extensions page and see what they have to say, I have a seven-button mouse. Thanks

---

### Post by vasa1 on 2017-11-18
Please see if
[https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=20#p1388277](https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=20#p1388277)
[https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=20#p1389053](https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=20#p1389053)
[https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389440](https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389440)
[https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389747](https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389747)
[https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389891](https://forums.linuxmint.com/viewtopic.php?f=47&t=257217&start=40#p1389891)
are of any help. I don't use mouse gestures and so can't evaluate those posts!

Re Foxy Gestures, I came across: [https://github.com/marklieberman/foxygestures](https://github.com/marklieberman/foxygestures)> In OSX and Linux, the context menu is shown on mouse down. (Context menu on mouse up is the default for Windows.) When FireGestures is installed on OSX/Linux, it changes the context menu to be shown on mouse up. Web extensions cannot replicate this functionality. Due to the issue described in #4 right-button gestures work poorly in OSX/Linux.

An option to use a modifier key to start or ignore gestures is being developed. If you want to see a proper solution to this issue, please support [this Bugzilla entry]("https://bugzilla.mozilla.org/show_bug.cgi?id=1360278"). Update: the bug was accepted and is awaiting a user contributed patch. If you are available to help write this patch please contact me.

---

