---
title: "Firefox crashing with Gmail"
date: 2006-12-29
forum: General Help
---

### Post by radar1976 on 2006-12-29
I installed and configured an ATI 9000 AIW card.  I had a Rage 3D Pro card install before.  Everything worked fine with Gmail.

After getting X up and running, I now can not use firefox with gmail

the result is the following

Open Firefox, load mail.google.com  login page loads fine
when the login is successful, the inbox loads, shows up for a second and then firefox crashes

Here is a debug output I was able to capture, if you need more, let me know.

> ** Message: plugin_get_value 1 (1)

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
  (Details: serial 115 error_code 8 request_code 72 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by pay on 2006-12-29
You might need to open up a bug report. You could use gmail with Thunderbird or Evolution to prevent Firefox from crashing.

---

### Post by mjrclark on 2006-12-30
I vaguely remember having this problem a while ago. I think the solution was to remove flash! Do not ask me why, I cannot remember. I think it might have been a specific version, possibly beginning with g. I think what I did was remove the .so file from /usr/.mozillla/firefox/plugins (. indicates hidden files- reveal with ctrl+h I think) or similar, then downloaded a replacement off somewhere else.
My result might be very atypical, as I am using kubuntu and fudged the browser settings to replace Konquerer with Firefox 2. Not sure how I installed it or anything else relevant... I now have flash installed and working very well, so the replacement worked well,
Sorry I cannot be more specific in my recolation.

---

### Post by radar1976 on 2006-12-31
Issue solved...

I had libflashplayer.so and flashplayer.xpt in the same directory.  I removed flashplayer.xpt and it still crashes, switch them around, no issues at all.  The issue was libflashplayer.so file.

Cheers
Shaun

---

