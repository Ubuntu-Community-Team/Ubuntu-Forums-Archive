---
title: "rhythmbox hangs on startup using 100% CPU"
date: 2006-10-26
forum: General Help
---

### Post by hotani on 2006-10-26
I have about 5000 songs, on startup rhythmbox hangs and hogs the CPU for about 5-10 minutes. After that it is normal. Is this another Edgy "feature"?

It only does this on one machine. However, the other machines I'm using it on do not have as large a library. My work box has a few hundred songs on it and starts right up with no problem.

---

### Post by hotani on 2006-10-27
Here it is in all its glory (that green rectangle is my CPU monitor at 100%):
[img]http://hotani.net/images/screenshots/20061026_rhythmbox-hog.jpg[/img]

EDIT: I thought that maybe if I tricked it by renaming the music folder, then naming it back it would rescan and get on with doing its thing. The rescanning worked, and after an hour it had scanned all my music and was responsive. Then I closed it, opened it again, and it hung (see pic above). 

So rhythmbox in Edgy (like several other things I won't get into right now) is utterly useless. I was actually looking forward to using it now that it will edit tags. Maybe I'll come back and mess with it more once I get a kernel running that will recognize both CPUs.... ](*,) ](*,) ](*,)

Say it with me: "I LOVE EDGY!" Hello? Guys? Anyone?

---

### Post by hotani on 2006-10-28
This is fixed. It was apparently a result of [this problem](http://ubuntuforums.org/showthread.php?t=282956). So if you are having troubles booting the generic kernel and using the 386 version instead, stay away from rhythmbox until after running the fix in the thread linked above. 

[My other thread](http://www.ubuntuforums.org/showthread.php?t=285666) on this issue was probably a result of the same problem. Rhythmbox works perfectly now, kudos to frodon for posting the kernel fix.

---

