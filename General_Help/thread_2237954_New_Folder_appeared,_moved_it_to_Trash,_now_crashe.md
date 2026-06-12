---
title: "New Folder appeared, moved it to Trash, now crashes Ubuntu!"
date: 2014-08-04
forum: General Help
---

### Post by BlueAZ on 2014-08-04
Hi,   I've upgraded my AMD 64-bit desktop to 14.04 awhile ago.  I was frustrated by the lack of Ubuntu-Tweak and its great Janitor, so I used BleachBit (NOT as root!).  After that, I noticed a new folder in my Home directory called "slq7k_TPjm".  It appeared to be empty, so I moved it to Trash.  When I tried to empty Trash, my processor & disk started working like crazy and I got a message that the system was Preparing to empty the Trash.  This went on till it crashed the system.

I've tried various ways to figure out what this folder is, but even opening Trash starts the processor and disk activity, the MoBo alert starts going off, and I shut down to avoid a crash.  At one point I had it open long enough to open Properties on the folder, but it struggled to add up the size till the system went down again.  I ran Clam, but it came up with nothing.  If I start the system and don't open or try to empty Trash, everything works fine.

I'd like to be able to use the Trash folder.  How can I get rid of this strange folder there?

Many Thanks!

---

### Post by BlueAZ on 2014-08-14
Hi,    I found a solution to this in a thread about BleachBit on SourceForge.  Someone else used it, got the unknown folder, moved it to the Trash, then couldn't get it to empty.  A moderator recommended this:

In Terminal:   sudo rm -rf ~/.local/share/Trash/  

[FONT=arial]I did this, copying it exactly, and it worked!!  It took awhile, as the darn folder was around 450 Mb, but it didn't jam the processor & crash my system.  And after awhile, the Trash folder is finally empty!  Needless to say, I'll never use BleachBit again!

Hope this helps someone else![/FONT]

---

### Post by uRock on 2014-08-14
I had to stop using BleachBit when I installed ubuntu 14.04. It would would turn dark and stay that way for an hour if I let it. It works fine in my equivalent Linux Mint install, which I don't understand.

---

