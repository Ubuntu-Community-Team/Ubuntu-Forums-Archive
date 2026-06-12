---
title: "totem-video-indexer, 100% cpu usage, 3 load..."
date: 2007-11-05
forum: General Help
---

### Post by CrustyDOD on 2007-11-05
Hello!

Can someone tell me how to fix this problem if possible? totem-video-indexer is using all my CPU. I think it only starts to do this if i run KTorrent. I've also found this: 

[https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/137352](https://bugs.launchpad.net/ubuntu/+source/tracker/+bug/137352)

On top it says Fix Released, bottom post says tracker (0.6.3-0ubuntu1) which is the one i have right now. Where can i find fix for this?

---

### Post by jamiemcc on 2007-11-06
Its a bug in the torrent client - it affects tracker and beagle (and most likely strigi too) as it opens files in rw mode when it should open them in r (readonly)

if opened in rw mode, inotify will trigger beagle, tracker and other inotify monitors into thinking that the file has finished changing and hence cause constant indexing

Fix 1) make sure the directory for torrents downloads is a no watch directory or a crawl directory in tracker ( use a crawl directory if you still want it indexed)

Fix 2) report bug to the torrent client and get them to fix it

---

### Post by oysterpog on 2007-11-09
gday!

having the same problem. doesn't happen for long tho, cpu usage stays on 100% for about 2-3 minutes.

jamie what do you mean by watch/crawl directory in tracker? sorry i am a noob.

thanks in advance

---

