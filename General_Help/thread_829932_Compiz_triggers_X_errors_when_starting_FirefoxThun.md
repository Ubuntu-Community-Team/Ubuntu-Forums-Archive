---
title: "Compiz triggers X errors when starting Firefox/Thunderbird"
date: 2008-06-15
forum: General Help
---

### Post by merike on 2008-06-15
Occasionally when effects are enabled I'm unable to start Firefox and Thunderbird. When I disable Compiz then windows launch fine.

I usually get an error similar to the following one:
The program 'firefox-2-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 1833 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Running Hardy with KDE 3.5.9.

Any solutions to this?

---

### Post by jaygo on 2008-06-29
Hi,
I'm running kubuntu 8.04 with compiz-kde and firefox 3 out of the repo's without any issues. I would try disabling the compiz plugins a few at a time. Ah, I see you're using FF2 ... well that also worked for the two days I used it. Just checked -- still launches & loads fine.

---

