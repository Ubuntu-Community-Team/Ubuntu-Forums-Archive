---
title: "Serpentine Won't Burn CD"
date: 2006-11-16
forum: General Help
---

### Post by dschaller on 2006-11-16
I'm using Ubuntu 6.10 and cannot get Serpentine to burn an Audio CD. When I click "Write to Disc" nothing happens. Audio CD burning works fine from k3b and Serpentine worked fine with Breezy. Any ideas?

---

### Post by dschaller on 2006-11-28
I still have not solved this problem. Below is the traceback from Serpentine. Is there a way around the error at the end?

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/serpentine/mainwindow.py", line 522, in __on_write_files
    validate_music_list (self.music_list_widget.source, self.application.preferences)
  File "/usr/lib/python2.4/site-packages/serpentine/common.py", line 140, in validate_music_list
    if not preferences.pool.is_available (music["location"]):
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 227, in is_available
    if not on_cache and self.is_local(music) and self.is_wav(unique_id):
  File "/usr/lib/python2.4/site-packages/serpentine/converting.py", line 217, in is_wav
    return operations.syncOperation(is_pcm).id == operations.SUCCESSFUL
  File "/usr/lib/python2.4/site-packages/serpentine/operations.py", line 352, in syncOperation
    oper.start ()
  File "/usr/lib/python2.4/site-packages/serpentine/audio.py", line 468, in start
    self.oper.start ()
  File "/usr/lib/python2.4/site-packages/serpentine/audio.py", line 232, in start
    super (Gst09Operation, self).start ()
  File "/usr/lib/python2.4/site-packages/serpentine/audio.py", line 92, in start
    raise GstPlayingFailledError()
serpentine.audio.GstPlayingFailledError

---

### Post by StefanoCole on 2006-11-29
Hello, I have the same problem: with Dapper I was able to use Serpentine to burn CDs, now with Edgy I am not able, so I use Gnomebaker (still successful with Edgy).

Stefano

---

### Post by angelsneverdie on 2006-12-17
i'm having the same problem. . . anyone have a fix?

---

