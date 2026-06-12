---
title: "Gmail crashes Firefox after upgrade"
date: 2007-03-01
forum: General Help
---

### Post by okok on 2007-03-01
I upgraded from 6.06 to 6.10, and this included a firefox upgrade to version 2.

Now, a second after I use firefox to log into gmail, it simply disappears. I tried to disable all add-ons, but it made no difference.

Then I started firefox from a terminal window, and this is what accompanied its disappearance:

> 
** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

** Message: plugin_get_value 1 (1)

** Message: plugin_get_value 2 (2)

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
 (Details: serial 114 error_code 8 request_code 144 minor_code 3)
 (Note to programmers: normally, X errors are reported asynchronously;
  that is, you will receive the error a while after causing it.
  To debug your program, run it with the --sync command line
  option to change this behavior. You can then get a meaningful
  backtrace from your debugger if you break on the gdk_x_error() function.)


Any idea why this is so and what can I do to fix it?

---

### Post by jjj_uk on 2007-03-03
I'm experiencing the same problem

---

### Post by jjj_uk on 2007-03-03
:-)

The solution could well be to paste the text below into /usr/bin/firefox. I've got it as the first uncommented line. 

export  XLIB_SKIP_ARGB_VISUALS=1

It worked for me so I hope it will work for you too.

---

### Post by okok on 2007-03-03
Thank you very much! It worked. Any idea what it means, though?

---

