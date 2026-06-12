---
title: "Terminal FTP hash"
date: 2005-05-11
forum: General Help
---

### Post by npu on 2005-05-11
I can't figure out how to show the progress of an ftp file transfer with _ftp_ in Gnome-Terminal (in my case transferring files to my Xbox on a local network). When I used SUSE/konsole it was there by default.

My .netrc looks like this:
```
----$HOME/.netrc 600 perms --
machine 192.168.0.2
login xbox
password xbox
macdef
init
hash
lcd videos
cd E/Videos
```So, the hash-flag is on, but now a file transfer just floods the screen with #:s, instead of showing that nice line with percentage done and ETA. Everything works & the permissions are ok. Just doesn't look the way it should. I couldn't find an answer in the manual(s). There's remote support for this -- it's worked before. Anybody know what to do?

---

