---
title: "[SOLVED] Sound got quiet"
date: 2007-10-12
forum: General Help
---

### Post by TeeAhr1 on 2007-10-12
Something changed somewhere.  It started about two weeks ago, suddenly my sound (which had never had this problem before) was really quiet.  I went into alsamixer, and turned up PCM to 90, which helped some.  I don't have anything labeled "master" in there, but I do have "headphone," and that's maxed out, but at the bottom of the bar, there's a "00."  I don't know what that means.  KDE's volume control is maxed out also.  Any tips?

Thx-
Pete

---

### Post by reckless2k2 on 2007-10-12
i had this issue recently after upgrading from 3.5.6 to 3.5.7. i had to remove and reinstall alsa and then i was alright. the community docs related to trouble shooting sound will fix you right up.

---

### Post by TeeAhr1 on 2007-10-12
SOLVED.

Wow, that was easy, thanks for the pointer.  If anyone's searching this thread in the future, I simply removed alsa-base (it'll also remove the ubuntu-minimal dummy package, don't worry about it) and reinstalled it (and ubuntu-minimal, just in case one day a package check goes looking for it), and I was straight.  If you still have trouble, go into alsamixer in the command line and turn PCM up some.  If you're still having issues, here's the wiki page:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Thanks again, reckless2k2!

-pete

---

### Post by TeeAhr1 on 2007-10-14
Okay, not quite solved.  I can't get alsamixer to save my settings through reboot... :-[  Any advice?

-pete

---

### Post by Forgott3n on 2007-10-24
Take a look here to save alsamixer settings:

[http://ubuntuforums.org/showthread.php?t=207107](http://ubuntuforums.org/showthread.php?t=207107)

---

### Post by reckless2k2 on 2007-10-25
i'm glad i was able to help. 

mark it SOLVED....i'm racking up cups here. hahaha

---

