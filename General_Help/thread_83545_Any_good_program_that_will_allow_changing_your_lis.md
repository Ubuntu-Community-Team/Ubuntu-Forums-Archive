---
title: "Any good program that will allow changing your listening position in streaming audio?"
date: 2005-10-29
forum: General Help
---

### Post by schizoid_embolism on 2005-10-29
Hi everybody,

I am trying to find a program that will allow me to listen to a streaming audio file like this:

mms://arco.wmod.llnwd.net/a357/o2/cust10/WMHigh/May2005/rense_051805_hr2.wma

Right now, Firefox loads up Totem to handle this file, which works, except it does not allow me to change my listening position in the file like Windows Media Player does.  So if I miss something I want to hear, I have to start it all over from the beginning.  Any suggestions?

I have tried Beep and XMMS.  Beep shuts down immediately, and XMMS just pops up the file selection window, like it's looking for a file on my hard drive only.  I put the link in the "Play Location" option in XMMS and nothing happens.

Jeremy

---

### Post by bionnaki on 2005-10-29
do you have windows codecs & wma plugins installed for beep or xmms?

---

### Post by schizoid_embolism on 2005-10-29
Yes.  I am able to play the file just fine in Totem anyway.  I just can't change to another part of the file once I start playing it, like I can with Windows Media Player.

Jeremy

---

### Post by schizoid_embolism on 2005-10-29
Anybody?

---

### Post by bonzodog on 2005-10-29
you need the Xmms wma codecs, which I think should be in multimedia Universe. The gstreamer codecs for wma playback only work in totem. lok under xmms in Universe.

---

### Post by schizoid_embolism on 2005-10-29
Hmm, I can't seem to find it, there are tons of xmms files but none pertaining to wma that I can see.  I'm looking in Multimedia (Universe) in Synaptic.

Jeremy

---

### Post by schizoid_embolism on 2005-10-30
OK, downloaded a wma plugin ([This one](http://mcmcc.bat.ru/xmms-wma/xmms-wma-1.0.5.tar.bz2)) and installed from source, for both Beep and XMMS.  Both programs shut down when attempting to load that streaming wma file.

Beep's error message is this:
> Received SIGSEGV

This could be a bug in BMP. If you don't know why this happened, send a mail to us at [email]beepmp-devel@lists.sourceforge.net[/email]

Aborted


XMMS's error message is this:
> Segmentation fault

You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.


Is anybody else able to get that file to play or is this indeed a bug in both programs?

Jeremy

---

