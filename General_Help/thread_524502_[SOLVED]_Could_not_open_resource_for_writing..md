---
title: "[SOLVED] Could not open resource for writing."
date: 2007-08-13
forum: General Help
---

### Post by jusmurph on 2007-08-13
I can't get any sound?

Doing a Sound Preferences Test i get this:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

If i simply launch totem i get the following popup:
```
Could not open resource for writing.
```

Multimedia Systems Selection Tests
```
anth@smurph:~$ gstreamer-properties
ALSA lib pcm_ladspa.c:1503:(snd_pcm_ladspa_add_plugin) Unable to find or load plugin '(null)' ID 1773, path '/usr/lib/ladspa'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
ALSA lib pcm_ladspa.c:1503:(snd_pcm_ladspa_add_plugin) Unable to find or load plugin '(null)' ID 1773, path '/usr/lib/ladspa'
gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(625): gst_alsasink_open (): /pipeline0/alsasink3:
Playback open error on device 'default': No such file or directory]
ALSA lib pcm_ladspa.c:1503:(snd_pcm_ladspa_add_plugin) Unable to find or load plugin '(null)' ID 1773, path '/usr/lib/ladspa'

ALSA - Advanced Linux Sound Architecture: Could not open resource for writing.

```

---

### Post by jusmurph on 2007-08-13
/home/anth/.asoundrc

was the culprit...

---

### Post by acorey on 2007-09-02
Would have been helpful if you mentioned that one needs to comment out the un-commented line in ".asoundrc" 

Other than that, Thanks.

---

### Post by oldnat on 2007-10-29
Erm... which uncommented line?
...and... I do not have a .asoundrc file...?

I have the same error since installing the new nvidia driver (before that I did not have 2/3D acceleration)

---

### Post by jusmurph on 2007-10-31
> **oldnat said:**
> Erm... which uncommented line?
...and... I do not have a .asoundrc file...?

I have the same error since installing the new nvidia driver (before that I did not have 2/3D acceleration)

Its a hidden file.

Press Ctrl&h I think to be able to see it. I deleted it and it works fine.

It was me fiddling that inadvertently created it to begin with. So if you don't have the file, you may need to seek another solution.

---

### Post by cprice404 on 2007-11-29
Deleting/moving ~/.asoundrc fixed it for me too!  Can't believe how much time I spent trying other stuff before I found this thread.

And, it was also the case for me that I accidentally created that file by playing with some conf tool so I don't think my case was an out-of-the-box bug.

---

