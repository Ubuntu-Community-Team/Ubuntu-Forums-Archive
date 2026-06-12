---
title: "how to prevent uninterruptible"
date: 2007-06-15
forum: General Help
---

### Post by siva214215 on 2007-06-15
I am using Feisty.  There are few processess which go into uninterruptible status especially kswapd0, kjournald and the application currently running/just opened (firefox-evince).   When they are going into uninterruptible status the system goes dead slow ocassionally freezes for sometime.  the hard disk shows high disk activity while this happens.  The systems are having 256 MB of ram and it's usage never crosses 180-190 MB.

  If vm.swappiness can help then how much amount should I use.  This is happening mostly with sata drives.

Any kind of suggestions is appreciated.

---

### Post by guzdial on 2007-06-29
I have a similar problem.  Kpdf stopped working for me yesterday -- I'd double-click on a PDF file, and it would never show.  Today I started investigating with the system monitor open, and found that I had a bunch of "uninteruptible" kpdf processes.  I tried using Document Viewer (evince) instead, and it just became another uninterruptible process.  I opened Firefox to do a search on this problem, and keystrokes wouldn't show up in Firefox!  I found epiphany still worked, and that's when I learned that rebooting was my only hope out of uninterruptible processes.  I'm finding that I just can't use kpdf or evince anymore.  Xpdf and acroread work fine, so it's not the PDF file I was using.  Kile works still, too, so it isn't just KDE apps.  Any suggestions?

---

### Post by siva214215 on 2007-07-10
thank you guzdial for sharing.   I think it is all because of swapping from memory to hard disk.  I don't find any optimized vm.swappiness setting for this.  I tried in irc channel also.  No one is not understanding the problem, and they are just asking for any error messages from the logs.  I appreciate their work but no luck still now.

---

