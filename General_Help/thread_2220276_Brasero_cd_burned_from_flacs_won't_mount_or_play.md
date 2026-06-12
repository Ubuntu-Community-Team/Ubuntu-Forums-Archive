---
title: "Brasero cd burned from flacs won't mount or play"
date: 2014-04-27
forum: General Help
---

### Post by lou6 on 2014-04-27
I'm using the 3.10 brasero in xubuntu 14.04 to burn an audio cd from flac files. All appears normal, the cd is created but will not mount or play. Same result when I create bin/cue and burn that.

xfburn burns the same flac files and the resulting cd mounts/plays normally, so I know that gstreamer and other deps are present.

Any guidance or suggestions are welcome.

EDIT: some further info - I tried playing the offending cd in Parole and received this;

gstreamer backend error
could not handle cdda uri

Certainly explains why my cd player wasn't playing - it's expecting wav files...

Forgot to mention - a Brasero-burned cd of mp3 files mounts/plays normally so this problem appears to affect flac sources only.

---

### Post by lou6 on 2014-04-29
I've tried everything I can to solve this with no success including implementing the Schilling cdrecord/mkisofs fix. Still the same result - audio cd recorded from flac files will not play in any app or device.

---

### Post by Allavona on 2014-04-29
Brasero has been having issues for awhile now. One minute it'll work just fine, the next it couldn't burn a thing if it tried.

XFBurn has never failed to work for me.

---

### Post by lou6 on 2014-04-30
xfburn is very promising - I hope its developers will add disc-on-the-fly and a few other important functions without breaking the things it does now.

---

### Post by lou6 on 2014-06-10
I recently installed 14.04 from cdimage on a new machine. xfburn was updated to version 3.10 and now it will not write flacs to cd either...

is there a curse on ubuntu cd burners?

I also have imgburn installed via wine but that will not do the job either since it needs directshow filters (which are not supported by wine).

I finally broke down and installed k3b so (reluctantly) this thread is solved.

---

