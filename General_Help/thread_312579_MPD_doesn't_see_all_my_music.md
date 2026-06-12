---
title: "MPD doesn't see all my music"
date: 2006-12-04
forum: General Help
---

### Post by sinisterguy on 2006-12-04
Hello,

I've been having some problems with mpd. It doesn't seem to want to find all my music files. My library is a mixture of flac, ogg and mp3 files. I checked to make sure that mpd was built with support for those codecs, and it is. I also checked permissions and found that they checked out, but mpd still won't find those files. Here's result of ls -l for a file that mpd detects:

```
-rw-r--r-- 1 lukas audio 3348462 2006-11-13 21:14 Thousand Foot Krutch/The Art of Breaking/10 - Make Me a Believer.ogg
```

and one that mpd won't detect:

```
-rw-r--r-- 1 lukas audio 5491892 2006-11-12 16:18 Pillar/Broken Down: The EP/01 - Further From Myself (acoustic).ogg
```

this is really strange. Anyone have a solution?

---

### Post by tbroderick on 2006-12-04
Maybe it's you charset. Do you have your filesystem_charset set to UTF-8 or ISO-8859-1 in your mpd.conf?

---

### Post by sinisterguy on 2006-12-04
> **tbroderick said:**
> Maybe it's you charset. Do you have your filesystem_charset set to UTF-8 or ISO-8859-1 in your mpd.conf?
nope, that part's commented out in mpd.conf

---

### Post by tbroderick on 2006-12-04
> **sinisterguy said:**
> nope, that part's commented out in mpd.conf

Well, you should uncomment it and set it to UTF-8, delete your db, and then rebuild it with the new settings.

---

### Post by sinisterguy on 2006-12-04
> **tbroderick said:**
> Well, you should uncomment it and set it to UTF-8, delete your db, and then rebuild it with the new settings.
it still doesn't find the files :(

---

