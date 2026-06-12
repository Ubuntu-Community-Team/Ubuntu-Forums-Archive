---
title: "Firefox crashes after Automatix"
date: 2005-10-16
forum: General Help
---

### Post by kwaanens on 2005-10-16
I tried running Automatix on two computers. On my desktop computer it went OK on the first try. Everything seemed to be set up OK. (Even though I still have no sound, but that's the issue for another post)
Doing exactly the same on my laptop, Automatix got a "terminated with a child process [something]" several times. I tried changing a minimal amount of things at a time, and eventually Automatix told me that everything was installed OK. However, this was not the case, as the Debian menu still was not present. But I got that fixed.

The problem now is that, once I enter some sites Firefox crashes. I tried running Firefox from shell:
$ firefox
*** loading the extensions datasource
NP_Initialize
New
open dsp: Enheten eller ressursen opptatt < which means "Resource busy"
SetWindow
Destroy
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 31 error_code 165 request_code 143 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I'm guessing this is because of flash, so I tried removing the flash-mozilla and flashplayer-nonfree and installing libflash-mozplugin instead. However, the problem persists.

I had no crashes before Automatix. (Guess the point is, not to try to fix something that works...)

Does anyone have any thoughts on this?
Thanks!

- Ketil

---

### Post by kwaanens on 2005-10-17
I believe this magically fixed itself. I have no clue how. But at least flash doesnt crash firefox.

- Ketil

---

### Post by posu on 2005-11-06
i've got the same error when flashplayer-mozilla was not installed, though  libflash-mozplugin was installed. Just installed  flashplayer-mozilla and everything worked well.

---

