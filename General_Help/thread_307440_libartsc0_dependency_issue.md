---
title: "libartsc0 dependency issue"
date: 2006-11-26
forum: General Help
---

### Post by sadohert on 2006-11-26
So, I was trying to get myself setup to convert avi files to ipod format.  I had issues at many of the steps (no doubt on account of my lack of Linux experience) but I seemed to eventually get to a point where everythign SEEMed to work, but it turns out it didn't.
Here's the thread:
[http://ubuntuforums.org/showthread.php?t=114946&highlight=aac+support+in+ffmpeg](http://ubuntuforums.org/showthread.php?t=114946&highlight=aac+support+in+ffmpeg)

Anyway, I decided to go step by step through the whole process again, and hit a snag while trying install something.  I wanted to install:

sudo apt-get install libsdl1.2-dev

But this depends on libartsc0-dev, which in turn depends on libartsc0 version 1.4.3-0ubuntu1.

My repositories say I have both 1.4.3-0ubuntu1, and 1.5.1-0ubuntu0breezy1.  If I use synaptic to "force version" to the 1.4.3, Synaptic tells me a WHOLE WHACK of stuff will be removed.  An endless number of Kde type packages, etc.... this scares me.

What's goign on here?  I can't even find that 1.5.1-0ubuntu0breezy1 version in the packages (if I look up packages.ubuntu.com)... I'm way out of my league here, and considering trying to upgrade from Breezy to Dapper or Edgy.

Any help?

Thanks.

Stu

---

