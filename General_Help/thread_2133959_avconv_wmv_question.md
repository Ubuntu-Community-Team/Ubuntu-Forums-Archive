---
title: "avconv wmv question"
date: 2013-04-09
forum: General Help
---

### Post by AgentZ86 on 2013-04-09
Ok the files are located here:
[http://www.shepherdschapel.com/archive.htm](http://www.shepherdschapel.com/archive.htm)
right click and save link as

These are .wmv files

My command is like this:
avconv -i 4_5_2013.wmv  -b 128k 4_5_2013.wav
produces errors but the .wav file is fine

This is the error:
Error while decoding stream #0:0
[wmavoice @ 0x2175000] WMAPro-in-WMAVoice support not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.
[wmavoice @ 0x2175000] If you want to help, upload a sample of this file to [ftp://upload.libav.org/incoming/](ftp://upload.libav.org/incoming/) and contact the libav-devel mailing list.



I think it has something to do with the inability to write the ID3 tags to the file or something which would be ok but not really sure

---

### Post by andrew.46 on 2013-04-13
Same with the latest git FFmpeg I am afraid :(.

---

### Post by AgentZ86 on 2013-04-21
it's not creating a problem just wondered what the errors meant

---

