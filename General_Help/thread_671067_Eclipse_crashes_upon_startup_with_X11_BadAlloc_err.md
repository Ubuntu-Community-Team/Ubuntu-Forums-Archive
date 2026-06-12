---
title: "Eclipse crashes upon startup with X11 BadAlloc error_code 11"
date: 2008-01-18
forum: General Help
---

### Post by johj on 2008-01-18
Hello,

Today I stumbled into a very strange problem. After a hard reset of my laptop (a ThinkPad X61), [eclipse]("http://eclipse.org") suddenly won't start and crashes with the following error:

> 
$ ./eclipse 
The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 1078 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

This happens every time, and ONLY with eclipse. All other programs work fine. Please let me know if I should rather post this to some eclipse-related thread instead.

What's strange is that this worked perfectly just before the reset, though I do remember upgrading some packages just before the reset. I am able to start eclipse successfully inside Xnest, but not directly within Xorg. How can I debug this further? What could possible be wrong? I'm running Gutsy. Attached is my xorg.conf.

Any help appreciated

---

### Post by kladrian on 2008-01-18
same thing here
just after last updates i had to reboot and when i try to start eclipse again i get this:

The program 'Eclipse' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 422 error_code 11 request_code 146 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



any solutions?

---

### Post by PetePete on 2008-01-18
[http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse)

follow the downgrade instructions there.

---

### Post by johj on 2008-01-18
> **PetePete said:**
> [http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse](http://ubuntuforums.org/showthread.php?t=671020&highlight=eclipse)

follow the downgrade instructions there.

Thanks! :)

---

### Post by yogibear15 on 2008-01-18
security updates for gutsy now has version 2:1.3.0.0.dfsg-12ubuntu8.2 which fixes this problem (for Eclipse, at least).

---

### Post by stinkinrich88 on 2008-01-19
> **yogibear15 said:**
> security updates for gutsy now has version 2:1.3.0.0.dfsg-12ubuntu8.2 which fixes this problem (for Eclipse, at least).

How do we get that? I updated this morning and it's still doing it
thanks!

---

