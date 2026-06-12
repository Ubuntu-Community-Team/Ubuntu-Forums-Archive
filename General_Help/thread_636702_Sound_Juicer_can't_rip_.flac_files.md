---
title: "Sound Juicer can't rip .flac files?"
date: 2007-12-10
forum: General Help
---

### Post by bruban on 2007-12-10
I'm trying to use 'Sound Juicer' to convert a CD into .flac format files.

I'm using Ubuntu 7.10 with restricted formats installed.


When I try to extract (backup) my CD into .flac format files, I get the error message:


> Sound Juicer could not extract this CD.
Reason: File not found

Sound Juicer does recognise the CD correctly and will play tracks on it.

This is a clean install of Ubuntu 7.10.

I was able to do this OK with Ubuntu 7.04.

Any ideas?

---

### Post by mcduck on 2007-12-10
Have you installed the 'flac' package? I'm not sure if it is in the restricted extras..

---

### Post by bruban on 2007-12-10
Thanks for the reply.

Yes, I did install the flac package. However this did not make any difference when using Sound Juicer.

I haven't tried any command line options yet and won't be able to until tomorrow.

---

### Post by kpkeerthi on 2007-12-10
You would need a FLAC gstreamer pipeline. In Sound Juicer's Preferences dialog, select Edit Profiles. Add a new profile using New. 

```

audio/x-raw-int,rate=44100,channels=2 ! flacenc name=enc

```

---

