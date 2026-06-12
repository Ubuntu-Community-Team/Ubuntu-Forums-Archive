---
title: "Looking for GUI FTP Sync program"
date: 2015-05-28
forum: General Help
---

### Post by jiwon7258 on 2015-05-28
I want to synchronize my music folder in android device using FTP.
But I can't find GUI program which supports two way sync.
Is there any?

It should be GUI and supports two way sync

* I've used Freefilesync with curlftpfs but freefilesync doesn't work with error code 5

---

### Post by Lars Noodén on 2015-05-28
It's 2015 and [you really don't want FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), except maybe in a few unusual corner cases many of which can be avoided or worked around.  But that said, ...

You might be looking for something like [unison](http://www.cis.upenn.edu/~bcpierce/unison/) or the GUI for it, unison-gtk.  I stick with plain rsync which is one direction at a time so I haven't used it, but from what I read it meets the requirements of doing two-way syncing and having a GUI.  For plain rsync there is grsync.  Both unison-gtk and grsync are in the repository.

---

