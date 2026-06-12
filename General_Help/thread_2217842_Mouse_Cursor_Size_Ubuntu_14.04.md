---
title: "Mouse Cursor Size Ubuntu 14.04"
date: 2014-04-18
forum: General Help
---

### Post by garyzw on 2014-04-18
Any way to increase mouse cursor size in 14.04? I tries the old methods but the size changes when I move from desktop to applications. The new scaling feature is great but it did not affect the mouse.

---

### Post by mikelwrnc on 2014-04-30
Ever figure this out? Wrestling with this too.

---

### Post by ibjsb4 on 2014-04-30
I use dconf to change cursor size, should work for you.

[http://www.upubuntu.com/2012/10/how-to-change-mouse-cursor-size-and.html](http://www.upubuntu.com/2012/10/how-to-change-mouse-cursor-size-and.html)

---

### Post by grumblebum2 on 2014-04-30
See [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12994288#post12994288").
There's a new dconf **cursor-scale-factor** setting in 14.04.

---

### Post by Rasmus_Lock_Fuglsa on 2014-11-04
I have the same problem.

It seems the cursor-size is ignored for "the root" window, and there by all the default windows.

I found these issues:
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671121](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=671121)
[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1024482](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1024482)

But none of the "fixes" has worked so far.

---

### Post by Rasmus_Lock_Fuglsa on 2014-11-04
Note: Changing from lightdm to gdm according to this post:
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

Fixed the cursor-sizes (for me at least) - so, obviously, it's caused by the bug-reports I posted earlier.

---

