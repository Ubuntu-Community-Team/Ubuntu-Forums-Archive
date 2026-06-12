---
title: "Opera &amp; Motif"
date: 2005-08-05
forum: General Help
---

### Post by gingermark on 2005-08-05
Hi,

The only topics in the forum I found on this were regarding 64bit architectures, which worries me slightly, but anyways.

I installed Opera without difficulty on Warty, but I'm having troubles with Hoary. Opera installed fine, but requires Motif in order for other plugins to work. Motif doesn't appear to exist in the repositories, but Opera provides a .deb of OpenMotif which although intended for Debian should work for all Debian-based distros, at least that is according to them.

I downloaded the .deb and tried to install it, but it depends on another library, which is defunct. There were three possible replacements, but I have a certain reluctance to play around with Debian packages as I messed up my system that way when I first started using Ubuntu.

Opera also offered a binary tarball, and suggested that should be installed if the .deb package didn't work.

I tried installing it with the command they provided: "tar zxfv openmotif-2.1.30-linux-i386.tgz -C /"

I got the following response:

usr/
usr/X11R6/
usr/X11R6/bin/
usr/X11R6/bin/mwm
usr/X11R6/bin/xmbind
usr/X11R6/include/
usr/X11R6/include/bitmaps/
usr/X11R6/include/bitmaps/xm_error
usr/X11R6/include/bitmaps/xm_hour16
usr/X11R6/include/bitmaps/xm_hour16m
usr/X11R6/include/bitmaps/xm_hour32
usr/X11R6/include/bitmaps/xm_hour32m
usr/X11R6/include/bitmaps/xm_information
usr/X11R6/include/bitmaps/xm_noenter16
usr/X11R6/include/bitmaps/xm_noenter16m
usr/X11R6/include/bitmaps/xm_noenter32
usr/X11R6/include/bitmaps/xm_noenter32m
usr/X11R6/include/bitmaps/xm_question
usr/X11R6/include/bitmaps/xm_warning
usr/X11R6/include/bitmaps/xm_working
usr/X11R6/lib/
usr/X11R6/lib/X11/
usr/X11R6/lib/X11/app-defaults/
usr/X11R6/lib/X11/app-defaults/Mwm
usr/X11R6/lib/X11/system.mwmrc
usr/X11R6/lib/libMrm.so.2.1
usr/X11R6/lib/libUil.so.2.1
usr/X11R6/lib/libXm.so.2.1
usr/X11R6/man/
usr/X11R6/man/man1/
usr/X11R6/man/man1/mwm.1
usr/X11R6/man/man1/xmbind.1
usr/X11R6/man/man4/
usr/X11R6/man/man4/mwmrc.4
usr/doc/
usr/doc/openmotif-2.1.30/
usr/doc/openmotif-2.1.30/LICENSE
usr/doc/openmotif-2.1.30/OpenMotifEverywhere.html
usr/doc/openmotif-2.1.30/OpenMotifEverywhere.txt
usr/doc/openmotif-2.1.30/README.runtime
usr/doc/openmotif-2.1.30/mot-ug/
usr/doc/openmotif-2.1.30/mot-ug/ch01.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch02.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch03.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch04.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch05.ps.Z

gzip: stdin: unexpected end of file
tar: Read 1462 bytes from openmotif-2.1.30-linux-i386.tgz
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I don't really know what I'm doing, and I'd prefer not to mess up my system now after I just got it how I want it, so if anyone could tell me what to do next (aside from "use firefox") that would be most helpful.

Thanks,
gingermark.

EDIT: For anyone who cares (maybe someone who is having the same difficulty) I resolved the problem by installing libmotif3, motif-clients, and motifnls. I doubt I needed all three of them, and I'm not too sure which one did the job, but I don't much care and I'm too lazy to figure it out.

---

### Post by cowlip on 2005-08-10
[QUOTE=gingermark]Hi,

The only topics in the forum I found on this were regarding 64bit architectures, which worries me slightly, but anyways.

I installed Opera without difficulty on Warty, but I'm having troubles with Hoary. Opera installed fine, but requires Motif in order for other plugins to work. Motif doesn't appear to exist in the repositories, but Opera provides a .deb of OpenMotif which although intended for Debian should work for all Debian-based distros, at least that is according to them.

I downloaded the .deb and tried to install it, but it depends on another library, which is defunct. There were three possible replacements, but I have a certain reluctance to play around with Debian packages as I messed up my system that way when I first started using Ubuntu.

Opera also offered a binary tarball, and suggested that should be installed if the .deb package didn't work.

I tried installing it with the command they provided: "tar zxfv openmotif-2.1.30-linux-i386.tgz -C /"

I got the following response:

usr/
usr/X11R6/
usr/X11R6/bin/
usr/X11R6/bin/mwm
usr/X11R6/bin/xmbind
usr/X11R6/include/
usr/X11R6/include/bitmaps/
usr/X11R6/include/bitmaps/xm_error
usr/X11R6/include/bitmaps/xm_hour16
usr/X11R6/include/bitmaps/xm_hour16m
usr/X11R6/include/bitmaps/xm_hour32
usr/X11R6/include/bitmaps/xm_hour32m
usr/X11R6/include/bitmaps/xm_information
usr/X11R6/include/bitmaps/xm_noenter16
usr/X11R6/include/bitmaps/xm_noenter16m
usr/X11R6/include/bitmaps/xm_noenter32
usr/X11R6/include/bitmaps/xm_noenter32m
usr/X11R6/include/bitmaps/xm_question
usr/X11R6/include/bitmaps/xm_warning
usr/X11R6/include/bitmaps/xm_working
usr/X11R6/lib/
usr/X11R6/lib/X11/
usr/X11R6/lib/X11/app-defaults/
usr/X11R6/lib/X11/app-defaults/Mwm
usr/X11R6/lib/X11/system.mwmrc
usr/X11R6/lib/libMrm.so.2.1
usr/X11R6/lib/libUil.so.2.1
usr/X11R6/lib/libXm.so.2.1
usr/X11R6/man/
usr/X11R6/man/man1/
usr/X11R6/man/man1/mwm.1
usr/X11R6/man/man1/xmbind.1
usr/X11R6/man/man4/
usr/X11R6/man/man4/mwmrc.4
usr/doc/
usr/doc/openmotif-2.1.30/
usr/doc/openmotif-2.1.30/LICENSE
usr/doc/openmotif-2.1.30/OpenMotifEverywhere.html
usr/doc/openmotif-2.1.30/OpenMotifEverywhere.txt
usr/doc/openmotif-2.1.30/README.runtime
usr/doc/openmotif-2.1.30/mot-ug/
usr/doc/openmotif-2.1.30/mot-ug/ch01.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch02.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch03.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch04.ps.Z
usr/doc/openmotif-2.1.30/mot-ug/ch05.ps.Z

gzip: stdin: unexpected end of file
tar: Read 1462 bytes from openmotif-2.1.30-linux-i386.tgz
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now

I don't really know what I'm doing, and I'd prefer not to mess up my system now after I just got it how I want it, so if anyone could tell me what to do next (aside from "use firefox") that would be most helpful.

Thanks,
gingermark.

EDIT: For anyone who cares (maybe someone who is having the same difficulty) I resolved the problem by installing libmotif3, motif-clients, and motifnls. I doubt I needed all three of them, and I'm not too sure which one did the job, but I don't much care and I'm too lazy to figure it out.[/QUOTE]
 Yep, it is libmotif3 that works with Opera :D I'm sorry I coldn't help u earlier!

---

