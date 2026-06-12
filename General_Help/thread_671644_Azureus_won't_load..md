---
title: "Azureus won't load."
date: 2008-01-18
forum: General Help
---

### Post by Pandemic187 on 2008-01-18
I tried to launch it in a console, and this is what I see:
```

Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 316 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
bob@BobsLaptop:~$ azureus
Looking for and picking a preferred Java runtime
Use environment AZUREUS_JAVA to override
Using Java: /usr/lib/jvm/java-7-icedtea/jre/bin/java
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
The program 'SWT' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 316 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
Can anyone make sense of this?

---

### Post by samosamo on 2008-01-19
Did you google "serial 316 error_code 11 request_code 146 minor_code 5"

May I recommend Deluge as a torrent client?  Some people like kTorrent as well.

---

### Post by pPrdrm on 2008-01-19
Hi Pandemic187,
Did you update xorg recently? Read this thread: [[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=670942&highlight=vlc[/COLOR]]("http://ubuntuforums.org/showthread.php?t=670942&highlight=vlc"). Maybe it's the solution to your problem. Let us know if it helped.

---

### Post by Ocxic on 2008-01-19
make sure your installing the version 3 or Vuze from sourceforge, i found most of my problems went away after that.

---

