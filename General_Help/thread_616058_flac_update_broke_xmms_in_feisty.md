---
title: "flac update broke xmms in feisty"
date: 2007-11-17
forum: General Help
---

### Post by jamvegan on 2007-11-17
Since the recent flac security updates I am no longer able to play flac files in xmms.  I found a thread indicating that this is the case in gutsy, but I'm running feisty.  xmms-flac is installed (and I tried reinstalling it--no change).

Does anyone know how I can get xmms to play flac again?  That's how I rip most of my sound files.  (And I've seen many recommendations for other music players, and have tried several, but I just like xmms. *shrug*)  Thanks!

---

### Post by ske1fr on 2007-11-18
Yes, I just like xmms and it's simplicity too.  See [http://ubuntuforums.org/showthread.php?t=272625]("http://ubuntuforums.org/showthread.php?t=272625")  for a temporary solution.  A bug report has been filed.  It affects Dapper too.

---

### Post by jamvegan on 2007-11-18
Thank you!  Downgrading libflac7 and xmms-flac as described in that post worked for me (and all of my .flac files are ripped from my own CDs, so the security vulnerability should be a non-issue for me).

---

