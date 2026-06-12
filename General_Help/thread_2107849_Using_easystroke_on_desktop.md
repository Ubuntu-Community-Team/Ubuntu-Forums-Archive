---
title: "Using easystroke on desktop"
date: 2013-01-22
forum: General Help
---

### Post by Odzinic on 2013-01-22
I recently discovered easystroke and have been creating some gestures, but when I try a gesture on my desktop (with Mouse Button 1) I get the highlight/select orange box that occurs when holding down button 1 and moving those mouse.

Is there a way to disable this orange box or another workaround? I'm using gnome.

---

### Post by stinkeye on 2013-01-23
Not a good idea to use button1.
Default is middle click which I change to mouse3,(right mouse).
Just need to not pause too long after completing the gesture so as not to initiate
the right click context menu.

[**_[COLOR="darkred"]easystroke wiki[/COLOR]_**]("http://sourceforge.net/apps/trac/easystroke/wiki/Documentation")
[**_[COLOR="DarkRed"]Keyboard shortcuts to mouse buttons using easystroke[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")

---

### Post by Odzinic on 2013-01-23
> **stinkeye said:**
> Not a good idea to use button1.
Default is middle click which I change to mouse3,(right mouse).
Just need to not pause too long after completing the gesture so as not to initiate
the right click context menu.

[**_[COLOR="darkred"]easystroke wiki[/COLOR]_**]("http://sourceforge.net/apps/trac/easystroke/wiki/Documentation")
[**_[COLOR="DarkRed"]Keyboard shortcuts to mouse buttons using easystroke[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10495426&postcount=11")

When I use button 3, it opens up the right click menu even when I do the shortcut quickly.

---

### Post by coldcritter64 on 2013-01-23
> **Odzinic said:**
> When I use button 3, it opens up the right click menu even when I do the shortcut quickly.
There is a setting to adjust the click timeout or disable it altogether, by disabling it totally if I hold the right button down and move the mouse I can "draw" all over the desktop until the right mouse button is released. To get the context menu on the desktop ensure the mouse is stationary, right click then release, you will then get the menu. Cheers.

---

### Post by stinkeye on 2013-01-23
As coldcritter64 said, try conservative or disable timeout.

---

### Post by Odzinic on 2013-01-24
> **coldcritter64 said:**
> There is a setting to adjust the click timeout or disable it altogether, by disabling it totally if I hold the right button down and move the mouse I can "draw" all over the desktop until the right mouse button is released. To get the context menu on the desktop ensure the mouse is stationary, right click then release, you will then get the menu. Cheers.

This still will not work for me. As soon as I right click the menu pops up and the gesture is not shown at all when I move the mouse even with those settings selected.

---

### Post by stinkeye on 2013-01-24
> **Odzinic said:**
> This still will not work for me. As soon as I right click the menu pops up and the gesture is not shown at all when I move the mouse even with those settings selected.

What release and desktop are you using.
When timeout is off the menu should only appear on button release
when not drawing a gesture.

---

### Post by Odzinic on 2013-01-25
> **stinkeye said:**
> What release and desktop are you using.
When timeout is off the menu should only appear on button release
when not drawing a gesture.

I'm using 12.10 and my desktop is GNOME 3.6.

---

### Post by stinkeye on 2013-01-25
Works fine here on 12.10 in Unity.

Test the settings in nautilus with various timeouts.
Hold down the right mouse without moving or releasing.
The delay before the pop-up appears should be noticeable using "conservative"
and shouldn't appear at all with "timeout off" until button release.

Are you seeing the gesture line drawn on the desktop.

---

### Post by Odzinic on 2013-01-26
> **stinkeye said:**
> Works fine here on 12.10 in Unity.

Test the settings in nautilus with various timeouts.
Hold down the right mouse without moving or releasing.
The delay before the pop-up appears should be noticeable using "conservative"
and shouldn't appear at all with "timeout off" until button release.

Are you seeing the gesture line drawn on the desktop.

Thank you for your help, strinkeye. I think I realized what I was doing wrong.

I was not setting the proper command under the details column and that prevented easystroke from actually having an action. Once I set the "Details" section of a gesture it ended up working flawlessly.

Seems that this problem was just due to me not understanding how to set gestures for applications properly.

Thanks for all your help everyone.

---

