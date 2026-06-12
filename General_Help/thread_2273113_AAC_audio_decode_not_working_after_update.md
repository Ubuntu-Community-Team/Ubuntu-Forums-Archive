---
title: "AAC audio decode not working after update"
date: 2015-04-10
forum: General Help
---

### Post by rich1212 on 2015-04-10
A small problem but not for me.
Programs will not import any file/container that has AAC audio. The result is a crash with a SIGSEGV in avcodec_decode_audio4().

The 14.04 has been rock solid for a year so I just take updates without any extensive review.
This week I took one that included extras updates and poof.

It removed my Audacity, OpenShot, Blender, Ardour, VLC and several more AV programs that had worked for a year.
It thoughtfully left Banshee and Totem although crippled. This I fixed with a gstreamer rebuild.

On reloading from the software center Audacity and OpenShot I find that I can no longer import any media file that has aac audio without a crash.
If I convert the target file to use any other audio format ie mp3,AC3 etc there is no problem.
I can however export a file with aac audio without error. In short I can encode aac but not decode it.

I'm not going to reinstall any of the big programs until I get this worked out. My entire dlna server depends on aac audio, my daw mixdowns are aac switching is not an option. And compiling a real ffmpeg over the top of ubuntus fork will blow up sooner of later.

Any hints would be appreciated.

OH any yes all of my dependencies are met.
As it relates to OpenShot my Python and mlt are the same versions that were stable for a year.
Why did I post in general rather than media : I'm not sure it didn't blow-up my Python

---

