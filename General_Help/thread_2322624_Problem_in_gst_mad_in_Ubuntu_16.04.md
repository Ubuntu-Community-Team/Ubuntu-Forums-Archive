---
title: "Problem in gst mad in Ubuntu 16.04"
date: 2016-04-29
forum: General Help
---

### Post by Anes_P_A on 2016-04-29
Dear Friends,

Developed a software in python which uses Gstreamer for the working. We installed it and work on ubuntu 15.10. For that installed some components like

libmad0-dev,libmadlib-dev and gstreamer0.1* . But when upgraded to Ubuntu 16.04 after installing above packages not solve problem . Got error as

> 
Traceback (most recent call last):
  File "<string>", line 1, in <module>
  File "/usr/lib/python2.7/site-packages/dbr/dbr.py", line 22, in <module>
    main()
  File "/usr/lib/python2.7/site-packages/dbr/dbr.py", line 13, in main
    r = reproductor.Reproductor()
  File "/usr/lib/python2.7/site-packages/dbr/reproductor.py", line 27, in __init__
    decoder = gst.element_factory_make("mad", "mp3-decoder")
gst.ElementNotFoundError: mad


Please advise how can install mad  and avoid this error.

Waiting for fast advise

Thanks

Anes

---

### Post by mc4man on 2016-04-29
gstreamer0.10 is basically dead & was targeted for complete removal in 16.04. It appears that the job wasn't 100% completed but most of the plugins are gone. That would include the ugly & bad plugins, likely the ugly one provided mad.
You should port your software to gst-1.0 or re-create the ugly plugin (may or may not be possible

---

