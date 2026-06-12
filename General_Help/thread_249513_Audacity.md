---
title: "Audacity"
date: 2006-09-02
forum: General Help
---

### Post by ahaslam on 2006-09-02
[SIZE="2"]Is Audacity supposed to look like this, or is there something wrong? I find it very blocky and nothing seems to fit properly. If it's how it's supposed to be, can its appearance be altered with a different theme/skin?

[IMG]http://img232.imageshack.us/img232/8020/screenshotaudacitybp2.png[/IMG]

Tony.[/SIZE]

---

### Post by reacocard on 2006-09-02
Yep. that's how it is for me. no idea how to fix it.

---

### Post by ahaslam on 2006-09-02
Pretty naff really isn't it. It doesn't even try to fit in with the system theme.

It's a shame, it's the only recording app that I know of which is of any use. If it looked better, it would be a pleasure to use.

Tony.

---

### Post by Perfect Storm on 2006-09-03
Compile the latest which enable gtk2 (if you have libgtk2-dev package installed). It's quiet straight forward.

---

### Post by ahaslam on 2006-09-03
Are you referring to version 1.3.0b? I'd rather not run beta software, especially as I don't find the stable version all that stable (I lost 3 hours of audio last night - that's a lot to piece back together).

Tony.

---

### Post by ahaslam on 2006-09-03
I noticed that it could be run along side the stable version, so I gave it a go. I installed the development libiary that you mentioned and compiled wxGTK 2.6.3 fron source with no problems. I then started to complile the beta of Audacity. The configure process went smoothly, but durin make I encountered this error:
```
BatchCommands.o: In function `BatchCommands::ApplySpecialCommand(int, wxString, wxString)':/home/ahaslam/Desktop/audacity-src-1.3.0b-beta/src/BatchCommands.cpp:306: undefined reference to `ExportOGG(AudacityProject*, bool, wxString, bool, double, double)'
export/ExportMultiple.o: In function `DoExport':export/ExportMultiple.cpp:332: undefined reference to `ExportOGG(AudacityProject*, bool, wxString, bool, double, double)'
collect2: ld returned 1 exit status
make[1]: *** [../audacity] Error 1
make[1]: Leaving directory `/home/ahaslam/Desktop/audacity-src-1.3.0b-beta/src'
make: *** [audacity] Error 2
```
Any Ideas? This took a good 30 mins, can't be normal for such a small app :-k

Tony.

---

### Post by Perfect Storm on 2006-09-03
Try with the default wxGTK that comes with ubuntu

---

### Post by ahaslam on 2006-09-03
> **Artificial Intelligence said:**
> Try with the default wxGTK that comes with ubuntu
Exact same result :(

---

### Post by Perfect Storm on 2006-09-03
I'll take a look at it and see if I can sample a .deb package for you (as long you use i386).

---

### Post by ahaslam on 2006-09-03
Thanks, that would be greatly appreciated.

Tony ;)

---

### Post by Perfect Storm on 2006-09-03
Okay it's done. Tested on my computer. I've made it so it will get the diffrent libs to diffrent types of sound engines. I hope it's okay.

[http://www.filelodge.com/files/room38/1059449/Ubuntu/audacity_1.3.0b-beta-1_i386.deb](http://www.filelodge.com/files/room38/1059449/Ubuntu/audacity_1.3.0b-beta-1_i386.deb)

If I screw up the dependency please post back so I can correct it.

What's enable in my audacity:
> Finished configure:
LIBVORBIS: using SYSTEM libraries
LIBMAD: using SYSTEM libraries
LIBFLAC: using SYSTEM libraries
LIBSNDFILE: using SYSTEM libraries
LIBID3TAG: using SYSTEM libraries
LIBSAMPLERATE: disabled
LIBRESAMPLE: using LOCAL libraries
LIBSOUNDTOUCH: using LOCAL libraries
LIBNYQUIST: using LOCAL libraries
ladspa: enabled
audiounits: disabled
prefix=/usr/local


---

### Post by reacocard on 2006-09-03
your .deb wouldn't install for me. complained about an unsatisfyable dependency (wxgtk). so i built it myself. works great, and i have a checkinstall .deb if anyone wants it.

---

### Post by Perfect Storm on 2006-09-03
Can I get the exact output error, so I can correct it.

---

### Post by ahaslam on 2006-09-03
Thanks for your effort, unfortunately the .deb won't install for me either.

Here's the output:
```
ahaslam@ahaslam-laptop:~$ cd Desktop/
ahaslam@ahaslam-laptop:~/Desktop$ sudo dpkg -i audacity_1.3.0b-beta-1_i386.deb
(Reading database ... 134017 files and directories currently installed.)
Unpacking audacity-src (from audacity_1.3.0b-beta-1_i386.deb) ...
dpkg: dependency problems prevent configuration of audacity-src:
 audacity-src depends on libsamplerate0 (>= 0.1.2-2); however:
  Package libsamplerate0 is not installed.
 audacity-src depends on libalut0 (>= 1.0.1-1); however:
  Package libalut0 is not installed.
 audacity-src depends on flac (>= 1.1.2-3ubuntu1); however:
  Package flac is not installed.
 audacity-src depends on libfluidsynth1 (>= 1.0.6-4); however:
  Package libfluidsynth1 is not installed.
 audacity-src depends on libwxgtk2.6-0 (>= 2.6.3.2.1.1ubuntu2~dapper1); however:  Version of libwxgtk2.6-0 on system is 2.6.1.2ubuntu2.
dpkg: error processing audacity-src (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 audacity-src
ahaslam@ahaslam-laptop:~/Desktop$
```

Thanks again,
Tony.

---

### Post by reacocard on 2006-09-03
That's the error I got. Anthony, if you give me your email I'll send you my .deb for you to try.

---

### Post by ahaslam on 2006-09-03
Thanks, I've sent you my address.

Tony ;)

---

### Post by ahaslam on 2006-09-03
Thank you, your .deb worked perfectly :)

How did you get it to work? I tried to compile but came upon a wx related error, even though I had installed the latest stable version (see first page).

Thanks again, 

Tony.

---

### Post by Polygon on 2006-09-04
the deb does not install, it says unresovable dependencey libwxgtk2.6-0 and i have that installed. suggestions?

---

### Post by Perfect Storm on 2006-09-04
I'll rebuild it, it was made in a haste for Anthony Haslam. That's happen when you hurry too much :-/

---

### Post by PhrankDaChickenGeek on 2006-10-28
Could you please attach the DEB file to a post, instead of an external link? Some filters block that site.

Thanks much! :)

---

### Post by Perfect Storm on 2006-10-28
> **PhrankDaChickenGeek said:**
> Could you please attach the DEB file to a post, instead of an external link? Some filters block that site.

Thanks much! :)

I don't have it anymore.
Though it's not hard to compile it, it's straight forward. If you have problems just post it :)

---

### Post by reacocard on 2006-10-28
> **PhrankDaChickenGeek said:**
> Could you please attach the DEB file to a post, instead of an external link? Some filters block that site.

Thanks much! :)

I still have my .deb. Just send me your e-mail and I'll get it to you. I can't attach it here because it's too big. (~2MB)

---

### Post by got_nix on 2006-11-09
curious does anybody have the an i/o problem with audacity as it it detects none at all.. the default recorder app works though.. but i want audacity gonna be practicing on my guitar using my laptop cuase amps are making up too much noise in the house. :(

---

### Post by reacocard on 2006-11-09
> **got_nix said:**
> curious does anybody have the an i/o problem with audacity as it it detects none at all.. the default recorder app works though.. but i want audacity gonna be practicing on my guitar using my laptop cuase amps are making up too much noise in the house. :(

try doing
```
killall esd
```
before running audacity, and close any other applications that use the sound card (eg. music/video players).

---

### Post by tjk on 2006-11-29
> **reacocard said:**
> I still have my .deb. Just send me your e-mail and I'll get it to you. I can't attach it here because it's too big. (~2MB)

I haven't been able to install Audacity (beta), but after reading this thread I think that your .deb would solve my problem.  Do you still have it? (As I am a Linux newbie and it would be very helpful.)

---

### Post by reacocard on 2006-11-29
> **tjk said:**
> I haven't been able to install Audacity (beta), but after reading this thread I think that your .deb would solve my problem.  Do you still have it? (As I am a Linux newbie and it would be very helpful.)

Sure do. As above, just e-mail me and I'll send it to you.

---

### Post by wilberfan on 2006-11-30
I found this thread to be _really_ helpful in compiling the latest Audacity...

[http://www.ubuntuforums.org/showthread.php?t=199890](http://www.ubuntuforums.org/showthread.php?t=199890)

---

### Post by tjk on 2006-11-30
I found a different thread for Audacity and it didn't help at all.  In fact, something that I did while trying to install the beta source messed up all my other audio/vidio programs so that they eventually crash (including Audacity beta).  

I'm going to review the lib files as per the link that you give, but if anyone can help me out I'd appreciate it.  For example, is there a log file that would show me what may be causing the crashes? 

(I'm a newbie that has recently switch from MS&%#$@ to Linux -- and it looks like this will be a permanent change as (E/X)Ubuntu has greatly impressed me compared to distribs that I've tried over the last 10 or so years -- although I still get a little annoyed when I run into installation problems like this beta that had to be compiled from source with numerous dependent libs/etc)

---

### Post by Peepsalot on 2006-11-30
I was able to compile audacity, but I can't import any mp3's with it.  It says "This version of Audacity was not compiled with MP3 support."  Do I have to set some flags or something?  Anyone know how that works?

---

### Post by Perfect Storm on 2006-12-01
You need the right -devs that support mp3 while you compiling. You need to check ./configure output when compiling.

---

