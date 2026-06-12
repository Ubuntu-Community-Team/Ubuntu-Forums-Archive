---
title: "Thunderbird over ssh"
date: 2006-08-04
forum: General Help
---

### Post by spin2cool on 2006-08-04
From work, I like to be able to ssh into my box at home and run mozilla thunderbird to check several personal email accounts.

In the past, this worked with no problems.  I just 'ssh -X' in, then run 'mozilla-thunderbird'.  Recently, though, I began getting the following error:

```
The program 'mozilla-thunderbird-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 2222 error_code 3 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Reboots don't seem to help, and I'm having trouble figuring out how to reproducibly create the error.  Any ideas on what could be causing this?   (FWIW, Both machines run up-to-date versions of Dapper.)

---

