---
title: "Just installed Pitivi, got big error on run"
date: 2007-05-11
forum: General Help
---

### Post by mjpatey on 2007-05-11
I just installed the nonlinear video editor, Pitivi.  Running it from the terminal, I got:

~$ pitivi 
The program 'pitivi' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 119 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Anybody been here before?  Thanks for any help you may have.

-Mark

--edit: I installed it via apt-get, so I assume it's the approved version in the Ubuntu repos.

---

### Post by srt4play on 2007-05-11
I just installed it on my system, it runs fine.

Maybe try reinstalling it?

---

### Post by mjpatey on 2007-05-11
I just ran across this error in someone else's post, and it was suggested that we run it with the --sync switch.  I did that, and for whatever reason, it ran fine.

Now that I've used it a little, I can see it's in its very early stages of development.  I think I'll pass for now!  I do like how kdenlive is shaping up.  They both are showing promise.

---

