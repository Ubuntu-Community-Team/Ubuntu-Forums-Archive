---
title: "Need to sync folders across a network"
date: 2006-10-30
forum: General Help
---

### Post by Naegling23 on 2006-10-30
I have two computers connected to my home network, I would like to syncronize a few folders on each (so I can have current copies of music and pictures on each).  I'm looking for something similar to microsoft's fileshare.  I would prefer if this could be done automatically, but I could live with a manual sync.  Any suggestions?

---

### Post by tribaal on 2006-10-30
You're probably looking for something like 'rsync'. If you feel savy enough you can learn pretty much anything about it by ready it's man page ("man rsync" in a terminal), otherwise I suggest you start by reading [this post]("http://ubuntuforums.org/showthread.php?t=187894&highlight=rsync").

Hope this answers your concerns... :)

- trib'

---

### Post by Naegling23 on 2006-10-30
thanks, it actually looks like unison is what Im looking for.  Ill have to give it a try.  Basically, I try to have a "my documents" type folder, but I want current versions on each computer, so when one is updated, the other gets the latest version.  Its a cheap way for me to backup everything too.  rsync seems to be more of a backup utility?

---

### Post by tribaal on 2006-10-30
Correct, but you can set up your different computers so that they sync their folder(s) together since rsync will only transfer the difference between the two folders...
But if Unison does what you want in a more friendly way, go for it :)

- trib'

---

