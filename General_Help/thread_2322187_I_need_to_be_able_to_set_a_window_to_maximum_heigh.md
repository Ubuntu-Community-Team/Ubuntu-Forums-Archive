---
title: "I need to be able to set a window to maximum height and have it STAY THERE"
date: 2016-04-26
forum: General Help
---

### Post by 7-webmaster on 2016-04-26
Most window managers display windows in one of three sizes: normal, full-screen, and minimized (e.g. on the task bar).

Unity has FOUR sizes.  It adds a "snapped to max height/width" size.   But even though Unity temporarily displays the window in that size it  does not remember that I requested that the window be maximum height  or width.  This creates extra steps.  There is no way to get from  full-screen back to "snapped" size except by going to "normal" size and  then dragging the window to "snapped" size, again.  And then repeat that  the next cycle.  And then repeat that the next cycle. ad infinitum.

I want to make the "normal" size of a window the maximum height, but  Unity will not let me.  It keeps "restoring" the window to what Unity  insists is the "normal" size of the window, which is NOT the size that I  set it to.  This is frustrating.  If I make a window maximum height  then I damn well want that window to be maximum height, and not some  other size that Unity "thinks" is what I want.

How do I convince Unity that the "normal" size of a window IS the  maximum height, and NOT the size that I intentionally dragged the window away from.  Unity has a hell of a nerve ignoring my clear instructions!

---

### Post by mc4man on 2016-04-26
Has nothing to do with Unity. 
Windows that remember their previous size will work fine with what you described, some common examples are Firefox, Gedit & Nautilus.
Windows that don't,  won't & it's not Unity's responsibility to do so. In those cases you *may* be able to use the windows rules compiz plugin (- though any fooling around with rules is best done on a guest or disposable user session.
Otherwise some apps have their  default size defined in the app's source which then could be adjusted.

---

### Post by 7-webmaster on 2016-04-26
> **mc4man said:**
> Has nothing to do with Unity. 
Windows that remember their previous size will work fine with what you described, some common examples are Firefox, Gedit & Nautilus.
Windows that don't,  won't & it's not Unity's responsibility to do so. In those cases you *may* be able to use the windows rules compiz plugin (- though any fooling around with rules is best done on a guest or disposable user session.
Otherwise some apps have their  default size defined in the app's source which then could be adjusted.

My biggest problem is with Firefox, since I spend almost all my time on the web.  I am trying to tile my screen with Firefox windows so I stretch two windows to maximum height and 50% width.  But if I ever have to maximize one of those Firefox windows as soon as I try to restore it, by clicking on the third window manager button, the one that shows a rectangle when maximized, the fact that I previously dragged the window to maximum height is ignored and the window is resized to the height it had BEFORE I dragged it to maximum height.  I am annoyed that this window manager ignores my stated intention and refuses to honor my desire to tile the windows.

I do not have this problem on Windows and I do not have this problem with other window managers on Linux.  Only with Unity.  Unity has a "feature" that if you are dragging to resize a window toward the boundary of the screen frame that it helpfully pops the screen to maximum height or width, but this means that you cannot just drag the window to the screen frame because Unity takes over as you approach the frame and maximizes the displayed height or width without overwriting the default window size.  Hence my statement of the problem "I need to be able to set a window to maximum height and have it STAY THERE".

---

### Post by mc4man on 2016-04-26
Firefox is a good example because it's very straightforward.

It **always** opens to the window size of the last closed instance.
If not manually resized after opening as a not-maxed window,   the restore/max button maxs the window, re-clicking  returns the window to it's opening size.
 If  FF opens maxed then it restores to last saved not-maxed window size

As far as 'snap to'  - 
There is snap to top ( maximize, merge window deco into panel
snap to side - give max height, 1/2 screen width, don't merge window deco

So if you wanted FF to open maxed you need to last close it maxed. As mentioned if it opens maxed then it will restore to last saved,  not-maxed size
If you want FF to open 1/2 screen then you need to close it at 1/2 screen (last closed instance
If you want it to restore to 1/2 screen size then the last closed not-maxed FF must be 1/2 size (- never last close a manually resized FF window

---

### Post by 7-webmaster on 2016-04-27
> **mc4man said:**
> Firefox is a good example because it's very straightforward.

It **always** opens to the window size of the last closed instance.
If not manually resized after opening as a not-maxed window,   the restore/max button maxs the window, re-clicking  returns the window to it's opening size.
 If  FF opens maxed then it restores to last saved not-maxed window size

As far as 'snap to'  - 
There is snap to top ( maximize, merge window deco into panel
snap to side - give max height, 1/2 screen width, don't merge window deco

So if you wanted FF to open maxed you need to last close it maxed. As mentioned if it opens maxed then it will restore to last saved,  not-maxed size
If you want FF to open 1/2 screen then you need to close it at 1/2 screen (last closed instance
If you want it to restore to 1/2 screen size then the last closed not-maxed FF must be 1/2 size (- never last close a manually resized FF window

This has nothing to do with closing and opening.  This is all in a single session.

I have arranged two windows side by side so that they each fill half of the screen.  Each window has been stretched to the maximum height, which means that Unity (it actually might be Compiz, I honestly don't know where one leaves off and the other starts) got involved and snapped the window to full height before I had finished dragging it.  I then find that I need to do something **temporarily** in one of the Firefox windows that **temporarily** requires maximizing that window,  When I then click on the third window manager button to un-maximize that window the window goes back to the **original** size, the size that it had **before** I dragged it to full-height, not to the size the window **actually had** when I clicked on the maximize button. So I have to manually stretch the window again to maximum height.  After several thousand times this gets really annoying.  I made a request to the Unity team to address this but the request was rejected and I have not received any suggestions of any way to work around this.

So how do I get the window manager (whether the problem is in Unity, or Compiz, or wherever) to restore the window to the size it **actually had** when I clicked on the maximize icon, rather than the size it hadbefore that?

It seems illogical to me that the un-maximize icon does not exactly reverse the action of the maximize icon considering that they are both in the same place.

---

