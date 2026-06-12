---
title: "gnome-cups-add crashes on freshly install edubuntu 6.06.1"
date: 2007-03-25
forum: General Help
---

### Post by maximk on 2007-03-25
I can't add new printer via gnome-cups-manager. When I click "New Printer" icon, gnome-cups-add starts, but after several seconds finishes unexpectedly without any messages.
But it's possible to see some warnings and X error message if start from terminal.
Here they are:

```
** (gnome-cups-add:10853): WARNING **: Two ppds have driver == 'foo2zjs (recomme nded)'
        ->linuxprinting.org-gs-builtin/Generic/Generic-ZjStream_Printer-foo2zjs. ppd (Generic ZjStream Printer Foomatic/foo2zjs (recommended)[1]) and
        ->Generic-ZjStream_Printer.ppd.gz (Generic ZjStream Printer Foomatic/foo 2zjs (recommended))[1]

```

... repeated several times for different printer models and then:

```

The program 'gnome-cups-add' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 218 error_code 2 request_code 94 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by Heretic666 on 2007-03-30
I have same trouble, and discover that it is locale problem. I solve it this way: > michael@ubuntu:~$ LANG= gnome-cups-manager

---

### Post by maximk on 2007-03-30
**Heretic666**, thank you!

Your solution does really work!

And I think ubuntu-maintainer guys should take a look at this issue :)

---

