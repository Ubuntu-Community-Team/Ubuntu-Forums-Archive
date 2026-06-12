---
title: "Totem exiting on startup"
date: 2006-07-20
forum: General Help
---

### Post by AirRaven on 2006-07-20
Whenever I load a video or audio file in Totem, it loads, then quits inexplicably. I've absolutely *no idea* why it's started doing this.

I'm wondering if it's possible to reset it to the state it was in when I installed Ubuntu? Removing all config files as well?

---

### Post by Perfect Storm on 2006-07-20
Try start it through the terminal? And you have all that is required to run the specifics media file(s)?

---

### Post by AirRaven on 2006-07-20
> **Artificial Intelligence said:**
> Try start it through the terminal? And you have all that is required to run the specifics media file(s)?

When I run it through the terminal, I get this:
[quote=totem]The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 93 error_code 2 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
[/quote]

It worked in XGL/Compiz last time I logged in, I recall. I'll check it now.

---

### Post by AirRaven on 2006-07-20
Bizzarely, Totem works fine in my XGl session, but doesn't work at all on my vanilla GNOME session.

I used the installation script in [this thread](http://www.ubuntuforums.org/showthread.php?t=194993) to install XGl/Compiz if it's any help, which I doubt.

---

### Post by Perfect Storm on 2006-07-20
Sorry, I don't have any XGL experience so I can't you there.

---

### Post by H.E. Pennypacker on 2006-07-22
I am in the same position, except there are a few differences.  When I manually start Totem (through the menu), it opens up for a second or two, and then disappears.  There is no explanation for it doing this.  It just disappears.

If I double-click on a media file, and Totem is supposed to play it, Totem starts fine, and plays the file.  That's it.  It's just that Totem won't stay open when it is manually started.

Btw, this has nothing to do with XGL/AIGLX/Compiz for me.  It always does this.  Also, I use Totem-Xine.

---

### Post by Perfect Storm on 2006-07-22
If you havn't installed the diffrent libs that is needed: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Or you might try another player Mplayer and VLC are excellent choices and they works better than Totem.

---

### Post by PriceChild on 2006-07-22
Check it isn't xgl/compiz by switching user... choosing a "standard xserver" then trying again.

---

### Post by H.E. Pennypacker on 2006-07-22
I have solved my own problem (mentioned above) by following this bug report:

[https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229](https://launchpad.net/distros/ubuntu/+source/totem/+bug/35229)

---

