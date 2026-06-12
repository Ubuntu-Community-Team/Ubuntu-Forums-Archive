---
title: "Rhythmbox All Crashy"
date: 2008-01-25
forum: General Help
---

### Post by DoodlesQ on 2008-01-25
About a week ago, Rhythmbox started to get all crashy. After one song the window fades to black-and-white, though the song keeps playing. I have to xkill it and start over to listen to the next song (not a great way to enjoy an album).

The vagueness of the problem makes it difficult to troubleshoot. I don't know what other details to provide. I haven't switched up anything, besides installing the updates. I tried reinstalling Rhythmbox, but it didn't help. Anyone have any ideas?

---

### Post by jryprt on 2008-01-25
I was using Rhythmbox untell today Try Exaile its in Synaptic .
It has a Equalizer sounds better  than Rhythmbox.

---

### Post by lippman on 2008-01-25
I'm having a similar problem with Rhythmbox.  As I'm listening to music - typically shuffling through a playlist- eventually Rhythmbox segfaults.  Sometimes it writes a core file, usually not.  I can't find a common thread between the songs it's playing when it crashes (ie mp3 vs m4a vs m4a converted from m4p)

I've gotten it to re-create the error after launching from gdb (is it not written in C? does that make gdb worthless?) , here's the backtrace:

```
Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1323787376 (LWP 9301)]
0x00000000 in ?? ()
(gdb) backtrace
#0  0x00000000 in ?? ()
#1  0xb71976b4 in g_object_set_valist () from /usr/lib/libgobject-2.0.so.0
#2  0xb7197946 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#3  0xb513a097 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#4  0x087c2c00 in ?? ()
#5  0xb51433d2 in ?? () from /usr/lib/gstreamer-0.10/libgstplaybin.so
#6  0x00000000 in ?? ()

```

On a related note, I've tried Exaile, and it may be having the same problem.  After a bit of working, it closes.  Very similar to the Rhythmbox problem, but I haven't checked it as much.

---

### Post by DoodlesQ on 2008-01-27
I've tried virtually every MP3 jukebox program, but Rhythmbox was my favorite (until it started crashing). I don't like Exaile much, but I tried Banshee for a day. It also crashed reliably, though not as often as Rhythmbox. I'll have to test it more to try to find a pattern.

So maybe the problem is with GStreamer or something? I still have no idea how to fix it.

---

### Post by ackey on 2008-03-13
I've had some problems with slow response in Rhythmbox that I attribute to accessing my music through sshfs.  I only have had Rhythmbox crash, dump, and close once.  I wish it didn't have problems - it is by far my favorite player.

---

