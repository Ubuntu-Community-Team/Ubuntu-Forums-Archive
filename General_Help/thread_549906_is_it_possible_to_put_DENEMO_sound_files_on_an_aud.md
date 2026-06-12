---
title: "is it possible to put DENEMO sound files on an audio cd???"
date: 2007-09-13
forum: General Help
---

### Post by popepeter on 2007-09-13
is there any ubuntu 7.04 package that makes it possible to put denemo sound files on an audio cd so they cay be played in an ordinary cd player???

---

### Post by coggins on 2007-09-13
Denemo doesn't really do sound files AFAIK.  The sound you hear would be produced by either timidity or csound.    If it is timidity, then just save as a MIDI (from within denemo).  Then in the terminal type
```
timidity -Ow "/path/filename.mid" -o "/path/filename.wav"
```
obviously, replace "/path/filename.***" with the actual path and filename of your input and output files.  There may well be a program that can do this inside a GUI, but I haven't seen it.  I don't have any experience with csound but it should work much the same way.  If you are using csound as the backend of denemo, then save as .SCO from denemo.  Then you'll have to work out how to get csound to output to a file. ```
man csound
``` should help.

Now that you've made wave files, you can just use Serpentine to create an audio CD.

---

### Post by tonymoloney on 2007-09-19
Kmid will play midis from a GUI. It's in the Kubuntu Add/Remove Programs, so you should be able to get it in Ubuntu

---

