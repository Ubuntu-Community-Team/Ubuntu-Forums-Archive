---
title: "Rhythmbox Gstreamer &quot;Error while saving song information&quot;"
date: 2013-05-17
forum: General Help
---

### Post by EddyTheB on 2013-05-17
I try to change track information (artist name, etc) in Rhythmbox by right clicking on a song and choosing properties. But once I've made the changes and click close I get an error box that says:

Error while saving song information
GStreamer encountered a general stream error.

Any ideas? I had a quick look around and found similar errors, though not related to Rhythmbox, but none of the solutions appeared relevent. I did do this though...
```

 $ gstreamer-properties

(gstreamer-properties:24672): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:24672): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'

```

Perhaps that helps diagnose. 

Thanks.

---

### Post by JRBASTIEN on 2013-05-27
What version of Ubuntu and RB are you running?  I have the same issue since I upgraded from 12.10 to 13.04.  Any new album I have imported after the upgrade is missing the year information.  When I try to manually update it in the properties window, I get the same error as you.

I also have the long term release 12.04 with RB 2.96 and I don't have the issue on this system.

---

### Post by MacD on 2013-06-02
I am having the same problem editing song properties with RB 2.98 on Ubuntu 13.04.  The problem seems to be limited to files ripped from CD since the upgrade to 13.04

---

### Post by arverne73 on 2013-06-03
Same problem here (13.04 updated from 12.10, 64 bits)

---

### Post by iamzeroonline on 2013-06-08
same problem, ubuntu 13.04 64 bit

---

### Post by aracheldra on 2013-06-17
I'm also on 13.04 64-bit, and having the same problem. However, it only happens with music in MPEG4 ([FONT=courier new].m4a[/FONT] files); changing attributes of music in other formats works fine.

---

### Post by fffree on 2013-07-11
I have the same problem, 13.04 64-bit, and as aracheldra said it happens only with MPEG4 but not MP3 files.

---

### Post by AnGus_King on 2013-09-02
I also have the same problem, 13.04 64-bit

---

### Post by mynamesalex on 2013-09-08
Ubuntu doesn't officially support the commercially licensed MPEG formats (mp3/mpeg3,m4a/mpeg4).  From what I've studied, you have to download ubuntu-restricted-extras, or gstreamer0.10-plugins-ugly, to provided added functionality to play, read and control these files.  I have both packages installed and I can't change mpeg4 files either, my whole iTunes music library is all locked out on this OS; For properties changes only, I can still rock out :)

We'll have to wait for a bug fix.  I'm curious if they know about this minor glitch.

---

### Post by pauljwells on 2013-12-07
I have a nasty workaround. Install VirtualBox and a guest OS (I have Windows 7) Share the Music folder and then edit the tags in Explorer. Rescan the library back in Ubuntu and the tags are changed.

---

### Post by JRBASTIEN on 2014-01-19
Another workaround if you are patient is to manually edit the Rhythmbox database. It can be found here ~/.local/share/rhythmbox/rhythmdb.xml
To set the proper dates of the albums (on each individual songs), you will need to convert them in Rata Die format.

From Wikipedia again: Rata Die = floor (JD &#8722; 1721424.5) = (2455855.5-1721424.5) = 734431

Where JD is the Julian date.

Various sites offer Julian date converter like this one:  [http://www.onlineconversion.com/julian_date.htm](http://www.onlineconversion.com/julian_date.htm)

This is quite annoying.  No one has a fix or knows if this is reported somewhere as an issue?

And for those who are not sure:  Yes, editing m4a files worked perfectly before Ubuntu 13.04...

---

### Post by JRBASTIEN on 2014-01-26
For follow-up, I have filled out the following bug reports on Gnome Bugzilla:  [https://bugzilla.gnome.org/show_bug.cgi?id=723020](https://bugzilla.gnome.org/show_bug.cgi?id=723020)

---

