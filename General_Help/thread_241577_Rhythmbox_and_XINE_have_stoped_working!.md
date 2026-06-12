---
title: "Rhythmbox and XINE have stoped working!"
date: 2006-08-22
forum: General Help
---

### Post by slugkilla on 2006-08-22
Starting last week, my PC started acting strangely. First off, my 40 gig hard drive started to become full and I got the "95% full" pop up. So I deleted some apps with synaptic and deleted some old files by hand. After that I noticed that XINE stopped playing WMV and AVI, but mplayer still could. I started a thread for that and I was told to reinstall xine and the codecs and all that jazz. So I did this and XINE still does not work. Ok, that was not cool but I can use mplayer so no big deal. Then Rhythmbox stops working today! I pull it up and it pops up and then dies. I reinstalled it, but it does not work! What is with these failing apps? Is it possible that I have a virus? How can I "flush" my system of all this buggyness? Thanks in advance!

---

### Post by slugkilla on 2006-08-22
Here is the Rhythmbox output:

> 

(rhythmbox:7097): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:7097): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:7097): Rhythmbox-WARNING **: Unable to start mDNS browsing
The program 'rhythmbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3647 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


---

### Post by slugkilla on 2006-08-22
Hey! somebody has to know what is happening here! help me out.

EDIT: I used automatix to reinstall rhythmbox and it works now! Still XINE won't work and the mplayer plugin won't play wmv anymore.

---

### Post by DoctorMO on 2006-08-22
it's very unlikly that your system has a virus.

the problem with wmv support is that you need the win32codecs installed, if you have them installed sometimes the files are not in the right place or are not linked correctly.

ls /usr/local/lib/codecs/
ls /usr/local/lib/codecs/wmv*

if the wmv dlls do not apear here then mplayer/xince won't beable to play wmv.

I'm still not sure what is wrong with xine, have you deinstalled and reinstalled xine? it could be that you've removed files that are a part of another dependant package and screwed something up to the point where reinstalling xine isn't enough.

---

### Post by slugkilla on 2006-08-22
Yes. I did reinstall Xine. I put that code in a terminal and it outputed that  there is not no such directory. Is that the xine codec directory? If so then that explains a lot! Should I manually put the codecs there or do I need to install a package? Thank you so much for your reply.

EDIT: /usr/lib/codecs has codecs

---

### Post by slugkilla on 2006-08-23
I have also found that embeded videos no longer work either. Can someone give me a list of everything that could possibly fix this? Should I put the codecs in different places install extra packages, etc. This is really bugging me. I think that the only way to fix this is to do it manually. Any thoughts would help. Thanks

edit: for embeded videos, the mplayer thing comes ups, says "getting playlist" and then says "stopped" and that is all it will do. :(

---

