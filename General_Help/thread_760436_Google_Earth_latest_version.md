---
title: "Google Earth latest version"
date: 2008-04-20
forum: General Help
---

### Post by StOoZ on 2008-04-20
does anyone also experiencing the following issue with the latest version?
after installing it,  when I try to run it, I get the following error:
> Google Earth has caught signal 4.

Stacktrace from glibc:
  ./googleearth-bin [0x804f3c7]
  ./googleearth-bin [0x804f8ed]
  [0xffffe420]
  ./libbase.so(_ZN5earth17ScopedPerfSetting6createERK7QStringbb+0x64) [0xb70550f2]
  ./libbase.so(_ZN5earth17ScopedPerfSettingC2ERK7QStringbb+0x45) [0xb705518b]
  ./libbase.so(_ZN5earth20LogScopedPerfSettingC1ERK7QString+0x35) [0xb7055257]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application13setupQtLocaleEv+0x42) [0xb7273a60]
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x31) [0xb7273da9]
  ./googleearth-bin(main+0x2a1) [0x8050b77]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70a4050]
  ./googleearth-bin [0x804f201]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /home/nathan/.googleearth/crashlogs/crashlog-EFE0914A.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.

---

### Post by Vermind on 2008-04-20
Hello,
I installed the latest google earth from Automatix, and have had no problem with it. I am running Gutsy 64-bit with nvidia drivers.

---

### Post by StOoZ on 2008-04-20
what version is you latest version??

---

### Post by Pitel on 2008-04-21
According to [http://groups.google.com/group/earth-linux/browse_thread/thread/b2a5e6c3626e2937/667d8966147f01f0?lnk=raot](http://groups.google.com/group/earth-linux/browse_thread/thread/b2a5e6c3626e2937/667d8966147f01f0?lnk=raot) it's problem with missing SSE2 instructions in your (and mine) CPU. It's a shame, because you don't need SSE2 CPU in Win XP to run GE :(

---

### Post by StOoZ on 2008-04-21
WTF? so now I cant use Google Earth because I have a CPU from 2003? 
And I thought that google has a bit of sense ](*,)

---

### Post by scorp123 on 2008-04-21
I had similar problems ... I then deleted my ".googleearth" directory in my home folder. It seems I had some setting in there which caused GoogleEarth to crash. After having rid myself of that folder GoogleEarth works now for me. My CPU here is from 2002, a Pentium 4.

---

### Post by scorp123 on 2008-04-21
> **scorp123 said:**
> I had similar problems ... I then deleted my ".googleearth" directory in my home folder. It seems I had some setting in there which caused GoogleEarth to crash. After having rid myself of that folder GoogleEarth works now for me. My CPU here is from 2002, a Pentium 4. I just realised that you guys are talking about the really really newest version 4.3 that is available from Google and not the updated version 4.2 I recently upgraded from the repos. Hence please disregard my previous comment as it probably won't do any good. Sorry about that.

---

### Post by crazyred on 2008-04-22
I have the same problem as along with  many who have downloaded the latest version of GE on all distro's. I uninstalled and went to here [http://download.chip.eu/en/Google-Earth-Linux-Version-4.2_387112.html](http://download.chip.eu/en/Google-Earth-Linux-Version-4.2_387112.html)  and downloaded previous version and now have my GE back.

Cheers

---

### Post by dcstar on 2008-04-23
People, do not rely on 3rd party repositories for the latest version of Googleearth, the tools are already provided to do the job properly yourself:

[http://ubuntuforums.org/showthread.php?p=4769423](http://ubuntuforums.org/showthread.php?p=4769423)

---

### Post by Pitel on 2008-05-01
Google released minor update today, and it now works withous SSE2. Yeehaw!

[[img]http://farm4.static.flickr.com/3293/2457360440_340b6333f9.jpg[/img]](http://flickr.com/photos/pitel/2457360440/)

---

