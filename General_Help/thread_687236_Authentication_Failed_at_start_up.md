---
title: "Authentication Failed at start up"
date: 2008-02-04
forum: General Help
---

### Post by kejaba on 2008-02-04
SOLVED:  I had to delete the include common-pamkeyring from gedit /etc/pam.d/gdm

To get into the file without using Gedit, I used sudo nano and then the pathname



Hello.  I have searched the boards for this, sincere apologies if I have missed the answer.

I am a novice with Unix (but love Ubuntu).  In my last session, I installed Mac4Lin, and (probably more pertinently) followed the steps here to stop the nm-applet asking for a password

[http://ubuntuforums.org/showthread.php?t=187874](http://ubuntuforums.org/showthread.php?t=187874)

Now, when I try to log in, at the login prompt, I get an "Authentication failed" message with three dots in the username box.

First I tried the steps here:

[http://ubuntuforums.org/showthread.php?t=618331](http://ubuntuforums.org/showthread.php?t=618331)

I did CTRL ALT and F2, and changed the username and password

But when I rebooted I got the same error message.

I tried following the steps here [http://ubuntuforums.org/showthread.php?p=3605925](http://ubuntuforums.org/showthread.php?p=3605925)

But when I tried to do sudo dpkg-reconfigure gm, it said it was starting GNOME and took me back to the login prompt, with the error message.

When I try to do the thing suggested, by doing CTRL ALT F2 and then gedit /etc/pam.d/gdm and altering or commenting out lines, it says "cannot open display"

I am using Gutsy

---

### Post by RainKap on 2008-02-04
Excellent! I had exactly the same problem last night, after tweaking my Gutsy setup on my Acer Ferrari 4005 laptop, to get the wireless network to wake up after resuming from hibernation. I was on the point of cursing and doing a re-install, but decided to have a look on the forums first (fortunately I have a desktop PC as well as the laptop...).

You've saved me an hour or so of wasted time - thanks very much.

Ian

---

