---
title: "Cant make audio CDs."
date: 2006-07-28
forum: General Help
---

### Post by christhemonkey on 2006-07-28
I am unable to write audio cds using both serpentine and rhythmbox.

If i run serpentine in a terminal i get this output when i click 'Write to CD':
```
(serpentine:5749): GStreamer-CRITICAL **:
Trying to dispose element capsfilter9, but it is not in the NULL state.
You need to explicitly set elements to the NULL state before
dropping the final reference, to allow them to clean up.

```

If i run it with the -n option (to not use the gnomeVFS module) it gives this output:
```
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

```

This is using a HL-DT-ST CD-RW GCE-8481B disk drive.

I can burn information to CDs, but cannot make audio cds that are playable in my stereo!

Any advice would be very appreciated (i think my brother is going to kill me unless i get this working!)

---

### Post by jonrkc on 2006-07-28
Try k3b (a KDE app).  It works for me, for making audio CD's.  Another good tool for burning audio CD's is grip.  One of those ought to see you through this brother-crisis period, until you can find a fix for your other programs.

---

### Post by christhemonkey on 2006-07-28
Am just trying to get gnomebaker working.
I would use k3b, but as i dont have the internet on my ubuntu box, it would mean downloading and copying *all* the kde/qt libs across from here.

But i am trying an alternative now, thankyou.

---

### Post by christhemonkey on 2006-07-28
Argh, my brothers entire collection turns out to be in wma.

I think i may have to leave the pc converting over night using this script i found:
[QUOTE=uborka]
#!/bin/bash

current_directory=$( pwd )

for i in *.wma ; do mplayer -vo null -vc dummy -af resample=44100 -ao pcm -waveheader "$i" && lame -m s -v -V 0 audiodump.wav -o "`basename "$i" .wma`.mp3"; done

rm audiodump.wav
[/QUOTE]
Dont think that will work recursively either.
Hmr...

---

### Post by christhemonkey on 2006-08-03
Ended up burning the playlists in gnomebaker.
Though the playlist import feature does not seem to work *at all*.
So had to go through, find and add each track individualy.
Oh the fun...

---

