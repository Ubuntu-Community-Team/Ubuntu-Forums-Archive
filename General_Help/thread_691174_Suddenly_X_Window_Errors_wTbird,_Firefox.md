---
title: "Suddenly X Window Errors w/Tbird, Firefox"
date: 2008-02-08
forum: General Help
---

### Post by gaffin on 2008-02-08
I was waiting for my train this morning, happily browsing and reading email, closed up the laptop when the train arrived, reopened at the office and now I get this when I start Thunderbird or Firefox (fortunately Epiphany works, or I wouldn't be typing this):

```

$ thunderbird
The program 'thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 163 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

$ firefox
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 274 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Before trying to restart Thunderbird or Firefox, I upgraded to Firefox 2.0.0.12 via auto-upgrade.  I know a recent auto-upgrade broke my Java apps, so I wonder if the same thing is happening here.

Has anyone else seen this this morning?

thanks,
david

---

### Post by gaffin on 2008-02-08
rebooting fixed the problem.  don't know what was going on, but it's resolved now.

- david

---

