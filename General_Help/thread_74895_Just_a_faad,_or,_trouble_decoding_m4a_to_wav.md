---
title: "Just a faad, or, trouble decoding m4a to wav"
date: 2005-10-12
forum: General Help
---

### Post by gsmith on 2005-10-12
Looks like anything that can convert an m4a to a wav for me either is or uses faad.  I installed fad and am getting this dependancy issue when I try to use it:

```
faad: error while loading shared libraries: libmp4ff.so.0: cannot open shared object file: No such file or directory
```

However, I've no idea where to find this thing.  Anyone know where I can find it and how to set it up?

---

### Post by _cato on 2005-11-03
I got this error when I tried to use mythtv for playing audio-files.

I fixed this with extracting the lib manually from the .deb:

1) get the deb: wget [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/faad2/libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb)
2) uncompress part one: ar xf libfaad2-0_2.0.0+cvs20040908+mp4v2+bmp-0ubuntu2_i386.deb
3) uncompress part two: tar xzf data.tar.gz
4) copy lib: sudo cp usr/lib/libfaad.so.0.0.0 /usr/lib
5) create symlink: sudo ln -s /usr/lib/libfaad.so.0.0.0 /usr/lib/libfaad.so.0
6) register: ldconfig

---

### Post by gsmith on 2005-11-15
That didn't seem to change anything.

---

### Post by ArchVile on 2007-04-08
if anyone is still wondering about m4a decoding, mplayer (as usual) of course does the trick. (you could just play the file with mplayer as well.)

> mplayer -ao pcm:file=targetfile.wav sourcefile.m4a

technologically, no other player (mplayer is much more than a player, of course) comes even close to mplayer. and it makes using standalone decoders like faad obsolete for such simple tasks.

A/V

---

