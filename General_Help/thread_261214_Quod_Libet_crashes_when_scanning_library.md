---
title: "Quod Libet crashes when scanning library"
date: 2006-09-19
forum: General Help
---

### Post by drFUNK on 2006-09-19
Hello, I have an issue where  QuodLibet will crash after scanning about 1000 songs in my music library.  It worked last week, but I had to reinstall Ubuntu and ran into these issues.  I believe it has something to do with AAC support, because it read about 1/4th of my library perfectly before i added the gstreamer0.10-ugly-multiverse and gstreamer0.10-bad-multiverse packages.  The command line output is as follows: ```
jay@Mr-Bojangles:~$ quodlibet
Quod Libet is already running.
Unable to write to /home/jay/.quodlibet/control. Removing it.
Supported formats: flac, mp3, mp4, mpc, oggvorbis, wavpack
Loaded song library.
Opening audio device.
Checking /music/Music
**python: mp4atom.h:92: void MP4Atom::SetType(const char*): Assertion `(strlen(type) == 4)' failed.**
Aborted

```
I should also note that my collection is working fine with all songs loaded on Banshee, so it dosen't seem to be a bad-tagging issue.  Also, I have a friend who gets this same error message when launching Quod Libet (his library was previously loaded, but the program won't even launch now - it gives the same error to the command line), so it may just be a file that Quod Libet depends on that was not upgraded.  Thank you for reading.

---

### Post by hugmenot on 2006-09-20
Hey, this will be interesting for the developers of quodlibet I think (and likely only them). Just file a new ticket here (with details):
[http://www.sacredchao.net/quodlibet/newticket](http://www.sacredchao.net/quodlibet/newticket)

---

### Post by drFUNK on 2006-09-21
Update:  It seems that this isn't a quod libet error, rather something else on my system.  I tried uploading my library into Listen music player and recieved the same error.
> jay@Mr-Bojangles:~$ listen
/usr/lib/listen/main_window.py:104: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  try: self.resize(int(config.get("window","width")),int(config.get("window","height")))
/music/Music
NB FILE TO LOAD 4271
**python: mp4atom.h:92: void MP4Atom::SetType(const char*): Assertion `(strlen(type) == 4)' failed.**
Aborted

Does anyone have any idea of what I should attempt to update?

---

### Post by hugmenot on 2006-09-22
Listen is partly based on QL and surely uses Mutagen.
The ones likely to be on the know are the QL/Mutagen developers.

It could be the libmp4v2-0 package(?(?(?)))

---

### Post by drFUNK on 2006-09-24
> **hugmenot said:**
> Listen is partly based on QL and surely uses Mutagen.
The ones likely to be on the know are the QL/Mutagen developers.

It could be the libmp4v2-0 package(?(?(?)))

I tried re-installing the libmp4v2-0 package to no avail.  I filed a new ticket [here]("http://www.sacredchao.net/quodlibet/ticket/847") regarding my issue.  Thank you for your help!

---

