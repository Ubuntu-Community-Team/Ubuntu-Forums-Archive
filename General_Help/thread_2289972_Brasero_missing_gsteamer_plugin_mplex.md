---
title: "Brasero missing gsteamer plugin mplex"
date: 2015-08-08
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2015-08-08
I have all of these installed but i still get this error
[url=http://i.imgur.com/FOJpXV4.png]
  [img]http://imgur.com/FOJpXV4l.png[/img]
[/url]
* libmplex2-2.1-0 is also installed

the only thing i can guess is brasero is looking in the wrong place and needs a symlink to fix it

---

### Post by Yellow Pasque on 2015-08-08
If you're using Trusty, it's a known issue that didn't get fixed until later releases:
[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+bug/1239029](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad1.0/+bug/1239029)

---

### Post by mc4man on 2015-08-08
The last changelog to trusty explicitly mentions, wonder why?
> gst-plugins-bad1.0 (1.2.4-1~ubuntu1) trusty; urgency=medium

  * SRU Utopic update to trusty to get bugfix release 1.2.4 (LP: #1312305)
    + Don't hardcode /usr/share/sounds/sf2 path in fluiddec
    + hlsdemux: fails to compute media playlist URL if there is a query parameter
    + hlsdemux: fails to correctly parse CODECS and RESOLUTION
  * Don't enable mplex plugin.

 -- Iain Lane <iain.lane@canonical.com>  Fri, 25 Apr 2014 11:00:27 +0100

---

### Post by mc4man on 2015-08-08
It appears to be ok to have, don't know or use brasero often. If wanting to test then a build here for a short while. 
If so then any feedback on usability would be good.
(- also would like to know what brasero needs to trancode & author as it's current  recommends & suggests are a bit sparse. Like trancode & dvdauthor,  ?

[https://launchpad.net/~mc3man/+archive/ubuntu/fix-test](https://launchpad.net/~mc3man/+archive/ubuntu/fix-test)

---

### Post by Yellow Pasque on 2015-08-09
> **mc4man said:**
> The last changelog to trusty explicitly mentions, wonder why?

That baffled me too. Debian enabled it and then Ubuntu went out of their way to disable it when they synced from Debian. The only reason I can think of is a licensing issue, though Debian didn't seem to have a problem with it. *shrug*

---

### Post by pqwoerituytrueiwoq on 2015-08-09
> **mc4man said:**
> It appears to be ok to have, don't know or use brasero often. If wanting to test then a build here for a short while. 
If so then any feedback on usability would be good.
(- also would like to know what brasero needs to trancode & author as it's current  recommends & suggests are a bit sparse. Like trancode & dvdauthor,  ?

[https://launchpad.net/~mc3man/+archive/ubuntu/fix-test](https://launchpad.net/~mc3man/+archive/ubuntu/fix-test)
well that gets closer
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack Output set (AUDIO) image = /home/chad/Videos/tmp/brasero_tmp_FGJT2X.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_action
BraseroVob deactivating
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_session_output_size
BraseroVob Output set (AUDIO) image = /home/chad/Videos/tmp/brasero_tmp_Z6IT2X.cdr
BraseroVob called brasero_job_get_session_output_size
BraseroVob called brasero_job_get_action
BraseroVob called brasero_job_get_output_type
BraseroVob Got output type (is DVD 1, is SVCD 0)
BraseroVob Creating new pipeline
BraseroVob called brasero_job_get_current_track
BraseroVob called brasero_job_get_audio_output
BraseroVob can't create object : "Mpeg2enc" element could not be created 

BraseroVob stopping
Session error : "Mpeg2enc" element could not be created (brasero_burn_record brasero-burn.c:2856)
```

---

### Post by Yellow Pasque on 2015-08-09
Maybe mc4man needs to add this line to make sure mpeg2enc gets installed: [http://anonscm.debian.org/cgit/pkg-gstreamer/gst-plugins-bad1.0.git/commit/?id=1fef6e4b5f119b1dd9e39215a90555915c15de05](http://anonscm.debian.org/cgit/pkg-gstreamer/gst-plugins-bad1.0.git/commit/?id=1fef6e4b5f119b1dd9e39215a90555915c15de05)

---

### Post by mc4man on 2015-08-09
> **Temüjin said:**
> Maybe mc4man needs to add this line to make sure mpeg2enc gets installed: [http://anonscm.debian.org/cgit/pkg-gstreamer/gst-plugins-bad1.0.git/commit/?id=1fef6e4b5f119b1dd9e39215a90555915c15de05](http://anonscm.debian.org/cgit/pkg-gstreamer/gst-plugins-bad1.0.git/commit/?id=1fef6e4b5f119b1dd9e39215a90555915c15de05)
Yeah I just figured that out by comparing sources from working to trusty. The Debian folder has a separate  gstreamer-mpeg2enc.install file but the .so has to be part of the gstreamer-plugins-bad install. (weird way to do it...
So doing a test build elsewhere, if it works will copy over to that test ppa

(not for nothing but there are numerous other means to create this other than brasero, seems you need to burn a disk to test/ or does brasero have a create .iso only option?

---

### Post by pqwoerituytrueiwoq on 2015-08-09
i saw a .cue option, no iso though
if you think you got it working i can use a disk
i used devede to get the job done, but brasero said it was use 4.7GB of teh disk, while devede only uses 1/2 that
and i wonder if there is a quality difference in the video

---

### Post by mc4man on 2015-08-09
> **pqwoerituytrueiwoq said:**
> i saw a .cue option, no iso though
if you think you got it working i can use a disk
i used devede to get the job done, but brasero said it was use 4.7GB of teh disk, while devede only uses 1/2 that
and i wonder if there is a quality difference in the video
That's what's odd, without a dvd in the drive all one gets is a svcd image option. If a dvd is in the drive then the dropdown says Image File but it turns into SVCD image once selected, makes little sense

---

### Post by mc4man on 2015-08-09
For devede I'd look at the recent posts concerning devede-ng, ex.
[http://ubuntuforums.org/showthread.php?t=2288639](http://ubuntuforums.org/showthread.php?t=2288639)

---

### Post by mc4man on 2015-08-09
From what I can tell brasero is terrible for DVD_Video conversions. It will error out if any file is larger than DVD_VIDEO standard. 
**ERROR: [brasero] Horizontal size is greater than permitted in specified Level
5 yr. old bug
[https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/612251](https://bugs.launchpad.net/ubuntu/+source/brasero/+bug/612251)

---

