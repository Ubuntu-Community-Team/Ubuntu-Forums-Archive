---
title: "Wiley 15.10 64-bit - Nautilus Crashes when Dragging and Dropping Files"
date: 2015-12-09
forum: General Help
---

### Post by Kerry Lange on 2015-12-09
I'm using Ubuntu again.  I initially tried it out when it was Feisty Fawn.  Still very much a newbie, though I'm going to make it stick this time.  

When dragging and dropping files using Nautilus (or other file mgmt apps) the application crashes. I've read a couple of other threads in different forums on the same topic but they do not seem to apply to my situation, though I've gone to the trouble of re-installing Ubuntu as recommended by a couple of the respondents.

I'm running the latest version of nVidia drivers with dual monitors.  I've not done much since the initial install.  I've not installed anything exotic or done anything unusual that I recall.  I've updated Ubuntu using the update app as recommended.  

I recall one of the threads speculated that the issue is with compiz. One of the people in the thread had tried dragging and dropping without compiz running and Nautilus didn't crash.

When I run Nautilus from terminal, here's what the terminal tells me when it happens:

> kerry@kerry-All-Series:~$ nautilus Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory Please ask your system administrator to enable user sharing.

(nautilus:6283): Gdk-ERROR **: The program 'nautilus' received an X Window System error. This probably reflects a bug in the program. The error was 'BadWindow (invalid Window parameter)'. (Details: serial 4057 error_code 3 request_code 141 (Composite) minor_code 8) (Note to programmers: normally, X errors are reported asynchronously; that is, you will receive the error a while after causing it. To debug your program, run it with the GDK_SYNCHRONIZE environment variable to change this behavior. You can then get a meaningful backtrace from your debugger if you break on the gdk_x_error() function.) Trace/breakpoint trap (core dumped) kerry@kerry-All-Series:~$

---

