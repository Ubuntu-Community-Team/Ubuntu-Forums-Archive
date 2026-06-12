---
title: "Firefox fails unexpectedly"
date: 2007-01-26
forum: General Help
---

### Post by DLinn on 2007-01-26
Hi All- 1st post.

I have Unbuntu 6.10 installed and up-to-date and all's well except Firefox 2.0.0.1 Ubuntu-edgy.

When I run F'fox as user (only 1 and it's me) it runs for some non-reproducible period of time and then quits.
  It does not freeze but the whole F'fox she-bang shuts down.
  All other programs continue to run fine.
  If I restart F'fox I get a dialog to restart previous or start new... it will restart with either selection and the process repeat... runs for some non-reproducible time...
  Running F'fox as root (like now) no problems at all.

I ran F'fox out of a terminal window and got this:
" dlinn@dlinn-desktop:~$ mozilla
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
  (Details: serial 118 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

then:

"dlinn@dlinn-desktop:~$ firefox --sync
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
  (Details: serial 118 error_code 8 request_code 146 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)"

I have run it for as long as several hours without the quit and for as little as a one minute then poof (the magic dragon sorry:| 

I cannot interpret the error message. Any and all help will be appreciated.

Bye!

---

### Post by Buck2348 on 2007-01-26
Try this

[http://ubuntuforums.org/showthread.php?p=1672572](http://ubuntuforums.org/showthread.php?p=1672572)

Buck

---

### Post by igknighted on 2007-01-27
What extensions and plugins are you running?  It could be an issue with Flash (there are a lot) or some other extension... in fact that sounds the most likely.

---

### Post by fragos on 2007-01-27
To test for extension problems, disable them one at a time and see if the problem goes away.  To disable in Firefox: Tools-> Add-ons-> "Select an extension"-> Disable button will appear.

---

### Post by DLinn on 2007-01-29
Hello Again-

FINAL... I changed the video resolution to 24bpp and the problem has not occurred in 2 days.
Fix seems wild, peculiar, bizarre, unusual ...

No extensions or plugins are or have been installed.

Thank you :D :D  for your time and assistance.

DLinn

---

