---
title: "ran 'make' after './configure', but i made a mistake and  want to redo './configure'."
date: 2015-11-21
forum: General Help
---

### Post by averageschmoe on 2015-11-21
I've converted my HTPC from Windows to Ubuntu and was installing MakeMKV without really knowing what I was doing. Had I read ALL of the instructions on the MakeMKV website I would have seen that an optional step to enable 24-bit FLAC needed to be done prior to and during ./configure. Now that I've done that and 'make' but not 'sudo make install' can I somehow undo, delete, or otherwise start over the first two steps? Ultimately, I want to rerun './configure' with a bunch of options and arguments.

---

### Post by blm-ubunet on 2015-11-21
No harm done.
There are make options for this very scenario.
The configure process locates libraries & source files fills out the makefiles.

Run:
```
make clean
make distclean
./configure --new-options --more options
make
```

The 24bit flac option requires static build ffmpeg libraries ?

---

### Post by averageschmoe on 2015-11-21
I didn't even finish putting my kid to bed before I got a response making this my greatest tech support moment, ever. Thank you. 

Output from 'make clean' is ```
rm -rf out tmp
```
Is this what I want?

Output from 'make distclean' is ```
make: *** No rule to make target `distclean'.  Stop.
```
Good?

How would I determine if the commands did what I wanted? I want to make sure I'm starting from a clean state again before I ./configure with ffmpeg. 

Also, regarding your question about 24-bit FLAC requiring a static build of ffmpeg... According to MakeMKV's guide, yes. 
> Starting with version 1.8.6 MakeMKV no longer uses ffmpeg application,  but links directly to libavcodec. Please note that most distributions  ship a very outdated version of libavcodec (either from ffmpeg or libav  projects). You will have to compile a recent ffmpeg (at least 2.0) if  you need a FLAC encoder that handles 24-bit audio. Also you will have to  enable libfdk-aac support in ffmpeg in order to use AAC encoder.Here  are generic instructions for building makemkv-oss with latest ffmpeg:
- download ffmpeg tarball from [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html)
- configure and build ffmpeg:
```
./configure --prefix=/tmp/ffmpeg --enable-static --disable-shared --enable-pic --disable-yasm
```




---

### Post by steeldriver on 2015-11-21
How did you obtain the source code? if you're not convinced that 'make clean' is removing everything that it should, you can always start over from a fresh copy of the source code (unpacking a fresh copy of the tarball, or re-cloning the git repo or whatever)

---

### Post by averageschmoe on 2015-11-21
It's not that I'm not convinced, I just have no idea where or what to look for. I tend to over-think things so I'll just go ahead and re./configure and see how it goes.

---

### Post by averageschmoe on 2015-11-21
So I followed the MakeMKV instructions and the "Application fails to initialize." 
Here's the order I used:
```
cd ~/Downloads/ffmpeg-2.8.2
./configure --prefix=/tmp/ffmpeg --enable-static --disable-shared --enable-pic --disable-yasm
make install
cd ~/Downloads/makemkv-oss-1.9.7/
PKG_CONFIG_PATH=/tmp/ffmpeg/lib/pkgconfig ./configure
make
sudo make install
rm -rf /tmp/ffmpeg

```
This results in the above message, rebooting did not change the outcome.

---

### Post by blm-ubunet on 2015-11-22
The question about building ffmpeg for flac support wasn't really for my benefit..

I wouldn't go deleting the /tmp ffmpeg libav* before making sure makeMKV loads/works.

If "make distclean" has that error then there is no "distclean" option in the configure script.
I tried it here & there is no distclean option.

Did the output from configure seem okay?
Did the output from make seem okay? Errors?

You did build both parts of makeMKV ?
There are 2 different folders.
One part is linking a close source object code & the other is the open source GUI.

Does "makemkvcon" work?

You might wish to make use of the libmmbd libraries to aid other apps to play the optical disks directly.

---

### Post by averageschmoe on 2015-11-27
Thanks for the response. My work schedule and family life seem to pull me away from Ubuntu for about 5 or 6 days out of a week so getting anything accomplished -- much less actually learning anything -- is a rare feat. However, you were right, I didn't build both parts. I started from scratch on a different computer and slowly mucked my way through but I have successfully built a package from source and it wasn't nearly as scary as I thought. Hooray for Youtube tutorials that take the time to explain "what" and "why" steps are taken and what to expect when things don't go as hoped.

---

### Post by blm-ubunet on 2015-11-27
If you want to be able to play directly from the optical disk (without using streaming option) then checkout this topic:-
[http://www.makemkv.com/forum2/viewtopic.php?f=3&t=7009](http://www.makemkv.com/forum2/viewtopic.php?f=3&t=7009)
The topic is not just applic. to VLC.

---

