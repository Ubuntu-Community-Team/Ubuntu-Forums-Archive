---
title: "[SOLVED] Sound volume has decreased dramatically"
date: 2008-01-30
forum: General Help
---

### Post by bg1256 on 2008-01-30
As simply as I can put it:

I'm running Gutsy, and yesterday the volume of all my applications decreased dramatically.

My speakers are all the way up, and the volume on my computer is all the way up.

Both VLC and Exaile (my two primary media players) have their volume maxed as well. But, it's not nearly loud enough.

Can anyone give me some tips as to how to explore this problem?

---

### Post by Gannin on 2008-01-30
There are usually more volume sliders than just the main volume slider, so one of those could be down.  Have you tried checking out alsamixer on the command line yet?

---

### Post by bg1256 on 2008-01-30
Thanks, Gannin. It was the PCM in the alsamixer.  Somehow it got turned way down.

Thanks!

---

