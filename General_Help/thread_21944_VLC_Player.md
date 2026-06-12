---
title: "VLC Player"
date: 2005-03-24
forum: General Help
---

### Post by idn on 2005-03-24
Hey people, just thought I would let you know I had some problems with installing codecs with my Hoary AMD64 but I found VLC was available under apt-get. I use it in windows.

[VLC Site](http://www.videolan.org/vlc/ ) 

It plays pretty much everything right out the box, watching simpsons avi right now so you should get it now!

---

### Post by orion_114 on 2005-04-09
I also found vlc to be a great player. I got all the other ones to work on my system, nut I have a really low spec machine. 400 Mhz, 128MB RAM. I found that VLC ,although ugly, does the best job and works like a dream for playing files over my network.

---

### Post by nico1278 on 2005-04-09
Come on it is not so ugly. Didi you install the VLC for GTK, for me it is perfectly integrated to the gnome desktop.

---

### Post by idn on 2005-04-10
^ yeah i have the gtk version, goes really well with my theme.

---

### Post by lorap on 2005-04-10
yup,it's very easy to use and no need in additional codecs being installed.
it's very rare it wouln't play something.
moreover you'd install GVLC version,not gnome edition cause it has a bug but the version GTL+.choose this one once you decide install it.
if you choose VLC it wouldn't be added to Applications.so you'll need to add it to the panel yourself.
have a nice day!
pavel

---

### Post by whodat on 2005-07-26
Need help, how do I install this, I downloaded the tar.gz file from their site.  I extracted it to my desktop and now I'm stuck.

help a brother out. ](*,)

---

### Post by idn on 2005-07-30
You should really get it through apt-get:

sudo apt-get install vlc

that should do it all fine for you, and it should add a shortcut under the multimedia menu

---

### Post by gullf1sk on 2005-08-16
apt-get install vlc does not work for me :(
is there some file i can edit to add more sources apt gets its info from?
or is there a way to use apt to search for a program?
sorry if i seem a little dense, because i am :P

---

### Post by JacobVF on 2005-08-16
i love VLC in Win. and I'm trying to use it in Ubuntu as well, but I have no idea why this happens everytime I try to open a movie file... Any ideas?

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

### Post by lukemack on 2007-04-22
did you resolve this? i am getting a similar error:

---

