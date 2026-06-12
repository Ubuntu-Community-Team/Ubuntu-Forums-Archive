---
title: "Slow application loads"
date: 2005-08-02
forum: General Help
---

### Post by Chireru on 2005-08-02
After playing around with prelink (prelinking everything), all of a sudden a few applications load _VERY_ slowly (think: minutes).

Those applications are: OpenOffice and Lotus Notes (via Codeweavers Wine), but not IE (which is also under wine).

Since then, I've done a prelink -ua, which should have unlinked everything.

I've also tried reinstalling OpenOffice several times, which has no effect.

I've run out of ideas...  anyone got a clue what went wrong?

---

### Post by Chireru on 2005-08-03
Anyone have any ideas?  This is _very_ annoying..

Specifically, when starting OpenOffice, it loads to the point of having a window, the status bar says, "Loading Document" and hangs there at 0% for a few minutes then works fine.

Notes opens and displays the splashscreen, works for a little while (where I can dismiss the splash screen) then hangs for a few minutes.  It finally gives me a password prompt, then after entering my password, it hangs for another minute or so.

I can't think of how this would happen, since openoffice supports prelinking and prelinking wine apps shouldn't matter at all..

---

### Post by Chireru on 2005-08-03
After a little LD Debugging, this is the output of openoffice just prior to the hanging:

```
     13808:     binding file /usr/lib/libcups.so.2 to /usr/lib/libcups.so.2: normal symbol `httpGetHostByName'
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `gethostbyname' [GLIBC_2.0]
     13808:     binding file /lib/tls/i686/cmov/libnss_files.so.2 to /lib/tls/i686/cmov/libnss_files.so.2: normal symbol `_nss_files_gethostbyname_r'
     13808:     binding file /lib/tls/i686/cmov/libnss_files.so.2 to /lib/tls/i686/cmov/libpthread.so.0: normal symbol `__res_state' [GLIBC_2.2]
     13808:     binding file /lib/tls/i686/cmov/libnss_files.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `inet_pton' [GLIBC_2.0]
     13808:     binding file /lib/tls/i686/cmov/libnss_files.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `__strcasecmp' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `calloc' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `time' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /usr/lib/libcups.so.2: normal symbol `httpReconnect'
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `socket' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libpthread.so.0: normal symbol `fcntl' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libc.so.6: normal symbol `setsockopt' [GLIBC_2.0]
     13808:     binding file /usr/lib/libcups.so.2 to /lib/tls/i686/cmov/libpthread.so.0: normal symbol `connect' [GLIBC_2.0]
[it hangs here for a few minutes]
```

I'm thinking that either libpthread.so.0 or libcups.so.2 is corrupted..  I've reinstalled cups and all of it's related stuff, but glibc isn't an option in kynaptic, so I've reinstalled gcc and libc, but that didn't seem to fix it..

---

### Post by Chireru on 2005-08-04
After a bit of stubling around, it looks like it's CUPS that's probably causing the problem, so I'm guessing that it's /usr/lib/libcups.so.2.

What package is this in?  I've tried reinstalling everything cups several times, with no luck.  I'm about ready to reload this and start over...  it's _MINUTES_ to start openoffice and notes, and I can't print anything.

---

### Post by lakcaj on 2005-08-04
dpkg -S /usr/lib/libcups.so.2

---

### Post by Chireru on 2005-08-04
[QUOTE=lakcaj]dpkg -S /usr/lib/libcups.so.2[/QUOTE]
Thanks for the reply.  It's part of the "libcupsys2-gnutls10" package.

I have reinstalled that package several times.  Unfortunately, if I remove that package, it threatens to remove half the installed applications on the system.

I also noticed that CUPS is no longer running, when I try to run it manually, I get:
cupsd: Child exited with status 99!

Any ideas how I can get cups working again?

---

### Post by Chireru on 2005-08-04
After a bit of searching, now that I know it's CUPS, I've found that other people have had this problem several months ago, however, their solution didn't work for me:
[http://ubuntuforums.org/showthread.php?t=36515](http://ubuntuforums.org/showthread.php?t=36515)

---

### Post by Chireru on 2005-08-04
Figured it out.

For some reason, my loopback interface wasn't coming up, so cups couldn't bind to it, which caused everything else to wait a few minutes upon loading that library, for it to timeout the connection.

---

