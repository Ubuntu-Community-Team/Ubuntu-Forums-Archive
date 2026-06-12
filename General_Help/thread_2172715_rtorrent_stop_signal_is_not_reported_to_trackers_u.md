---
title: "rtorrent: stop signal is not reported to trackers upon exit"
date: 2013-09-06
forum: General Help
---

### Post by piramiday on 2013-09-06
I noticed that rtorrent 0.9.2/0.13.2 has a different exit procedure than previous versions: what happened before was that it distinguished a 'normal exit', CTRL+Q from the shell (or an INT signal), from a 'quick exit', CTRL+Q CTRL+Q from the shell (or a TERM signal), the difference between the two was the time spent to send 'stop' signals to the trackers in order to let them know that the client was disconnecting from the swarm. now, on the other hand, if I press CTRL+Q rtorrent exits 'quickly', without reporting to the trackers, and this happens even if I explicitly send an INT signal to the process.
what's happening? am I doing something wrong? did someone else notice the same issue?
any help's appreciated. :mrgreen:

---

