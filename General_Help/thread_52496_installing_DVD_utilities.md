---
title: "installing DVD utilities"
date: 2005-07-28
forum: General Help
---

### Post by OneSeventeen on 2005-07-28
dvrequant is a shell script someone over at linuxquestions.org wrote that automates the task of using mplayer / libdvdcss / transcode / mjpegtools / dvdauthor 0.6.10 / cdrecord (mkisofs) to rip, demultiplex, remultiplex, blah blah blah, burn DVD image.

I'd really like to use it on my ubuntu system, but when I search for transcode, I just find gtranscode, the gui interface for transcode.  (and since it's dependency, transcode, is not available, of course it won't install.)

so basically I've got mplayer, mjpegtools, dvdauthor, and cdrecord.

I need libdvdcss and transcode.

Any ideas how to install it?

---

### Post by amohanty on 2005-07-28
libdvdcss and transcode are in the backport repos (i386 afaik dunno about amd64).
Adding repositories:
[https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29](https://wiki.ubuntu.com/AddingRepositoriesHowto?highlight=%28repositories%29)
/etc/apt/sources.lst line:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

HTH
AM

---

### Post by OneSeventeen on 2005-07-28
That works great,
but now I'm getting an error installing transcode:

[quote=synaptic package manager]
transcode:

  Depends: libgcc1 (>=1:4.0.0-7) but 1:4.0-0pre6ubuntu7 is to be installed
[/quote]

I'm hesitant to do a --force-overwrite with packages that have stuff like libgcc in the name...

**EDIT:**Looks like my newbieshness is showing....  --force-overwrite is a dpkg thing, not an apt-get or synaptic thing...

Is there a way to get transcode to be okay with the libgcc1 that I already have, or will that mess things up?

---

### Post by amohanty on 2005-07-29
Look for ffmpeg
I think it supercedes transcode.

AM

---

