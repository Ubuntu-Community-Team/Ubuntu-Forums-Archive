---
title: "Stable install for 90+ days now has &quot;Cannot Find GRLDR&quot; error"
date: 2007-08-10
forum: General Help
---

### Post by prstl on 2007-08-10
[http://ubuntuforums.org/showthread.php?t=455078](http://ubuntuforums.org/showthread.php?t=455078)

The above thread deals with the GRLDR issue if you are attempting to perform a [COLOR="RoyalBlue"]WUBI INSTALL[/COLOR]:

My issue is [COLOR="Red"]NOT[/COLOR] occurring during an [COLOR="Red"]INSTALL[/COLOR]. 

I did a problem free install on an XP service pack 2 box first week of May 07.  Today I get the GRLDR error message and of course boot into XP and check the forums here.  While the information in the above listed thread is plentiful is was not helpful to me.

I image my hard-drives ever week just in case.  So while in XP, I renamed the WUBI folder to WUBI-old and then recovered just the saved WUBI folder from my disk image. Rebooted my machine and same error!

Since this is not an install problem and I have restored a good working image, what has changed since then?  I know from using WUBI for 90+ days that you must keep your hard drive defragged or it will fail to boot from time to time, so I know that this is not the problem.

I decided to perform a chkdsk on the drive and everything is back to normal. I booted back into XP, deleted the restored WUBI folder, renamed the WUBI-old folder back to WUBI, rebooted and all is still normal.

Lesson learned:  If you have a "working" install of WUBI that gets the GRLDR error, boot into XP and schedule a chkdsk before you do anything else.  If you have never used chkdsk, just google it and you will find it is a simple procedure to perform.  I hope this helps someone.

---

