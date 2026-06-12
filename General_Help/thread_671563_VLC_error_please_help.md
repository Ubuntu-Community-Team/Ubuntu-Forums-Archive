---
title: "VLC error please help"
date: 2008-01-18
forum: General Help
---

### Post by bizarrechaos on 2008-01-18
when i start vlc i get 

VLC media player 0.8.6c Janus
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 475 error_code 11 request_code 145 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

i have been messing with some audio video stuff today i unistalled totem and got mplayer to make the little video thumbnail icons and i also installed esound and mpg123-alsa for the mp3 mouse over preview those are the only things i can think of that might have affected this does anyone have an answer for me?
help is greatly appreciated thanks in advance

---

### Post by fyo on 2008-01-18
There are about a billion different threads on exactly the same topic, many of which are on the first page of threads in this very forum (so there's no excuse for not finding them) - and some of the topic names are VERY similar to yours.

That said, your problem *should* be solved by running update manager and making sure to update to the latest xserver-xorg-core (version ubuntu8.2)

---

