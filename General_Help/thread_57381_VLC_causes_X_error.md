---
title: "VLC causes X error"
date: 2005-08-16
forum: General Help
---

### Post by JacobVF on 2005-08-16
I'm trying to use VLC in Ubuntu, but I have no idea why this happens everytime I try to open a movie file... Any ideas? installed it via the apt get comand

jacob@MatildaL:~ $ vlc
VLC media player 0.8.1 Janus
[00000242] access_file access error: seeking too far
[00000269] mpeg_audio decoder: MPGA channels:2 samplerate:48000 bitrate:96
The program '.' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
(Details: serial 52 error_code 8 request_code 141 minor_code 17)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
jacob@MatildaL:~ $

---

### Post by bob k on 2005-08-23
I'm also getting this error.

---

