---
title: "Unison synchronized files are owned by root"
date: 2006-07-03
forum: General Help
---

### Post by Enigmatic on 2006-07-03
Is there some way to get around this, or am I doing something wrong? I'm syncing my mail betweeen laptop and desktop, and the files are all owned by root as default instead of by my user. It's a pain to have to go chown them later on.

---

### Post by aysiu on 2006-07-03
What command or program are you using to synchronize them?

---

### Post by Enigmatic on 2006-07-03
I'm using sudo unison /path on local/ /path on server/

If I try to just use unison, it's telling me that it can't read the cached information (I guess replica information, since it's owned by root). I'll see what happens if I delete that file and run as a normal user..

EDIT - works now!

---

