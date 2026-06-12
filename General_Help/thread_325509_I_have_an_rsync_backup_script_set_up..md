---
title: "I have an rsync backup script set up."
date: 2006-12-25
forum: General Help
---

### Post by Roasted on 2006-12-25
And I got this error when I did a "sudo backup" (backup = name of the rsync script).




total size is 60816185804  speedup is 70.55
rsync warning: some files vanished before they could be transferred (code 24) at main.c(791)
jason@jason:~$



I just ran it again. It didn't give me the error this time. I wonder what files could of "vanished?"

---

### Post by po0f on 2006-12-25
Roasted,

A quick google showed that other people are having this same problem, but it shouldn't be anything to worry about.  The culprit seems to be temporary files created during the rsync that are deleted before rsync gets to them.  Are you backing up your whole system with rsync?  If so, there are probably better solutions.

---

### Post by Roasted on 2006-12-26
No, all I'm backing up is my home folder, which includes my music, pictures, music videos, etc. Which... that's a GOOD bit of files, considering how much music and pictures I have. But this method is incredibly easy to do, so I'm a fan of it. As long as it's temporary files that are getting messed up and not something more valuable... then I'm okay with that.

---

