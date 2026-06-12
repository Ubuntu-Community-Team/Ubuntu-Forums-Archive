---
title: "stop motion animation"
date: 2005-03-23
forum: General Help
---

### Post by klaym on 2005-03-23
Hi!

I've been trying to find a good little program to aid me in stitching up a stopmotion animation. I will be making the animation with a normal digital camera (Nikon 4300). So I need an application that I can use to stitch it together, control the framerate, add some sound (via microphone and external audio files) and finally compile the animation as an MPG, AVI or something else. I haven't found many applications for my use, and some applications I just haven't gotten to work (Ganim8 for example).

So, any ideas on animation applications for Ubuntu? Especially if there's something in Ubuntu's repositories, I'd like to hear of those! Thanks!

---

### Post by orion_114 on 2005-04-08
With OpenOffice.org2 BETA you can export files to swf.
I am not sure how it handles sound though.

---

### Post by ed_agamemnon on 2005-12-21
i've run into this one [http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.htm]("http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/index.htm"), and just tried it 3 seconds ago on my Breezy Trial install and it didn't work:

> 
Selecting previously deselected package stopmotion.
(Reading database ... 61956 files and directories currently installed.)
Unpacking stopmotion (from stopmotion_0.3.1-1_i386.deb) ...
dpkg: dependency problems prevent configuration of stopmotion:
 stopmotion depends on libc6 (>= 2.3.2.ds1-21); however:
  Version of libc6 on system is 2.3.2.ds1-20ubuntu14.
 stopmotion depends on libgcc1 (>= 1:4.0.0-9); however:
  Version of libgcc1 on system is 1:4.0.0-7ubuntu6~5.04ubp1.
 stopmotion depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
 stopmotion depends on libtar; however:
  Package libtar is not installed.
 stopmotion depends on libvorbis0a (>= 1.1.0); however:
  Version of libvorbis0a on system is 1.0.1-1.
 stopmotion depends on libvorbisfile3 (>= 1.1.0); however:
  Version of libvorbisfile3 on system is 1.0.1-1.
dpkg: error processing stopmotion (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 stopmotion


can't be bothered to think right now... i'll have a play later :)

---

### Post by ed_agamemnon on 2005-12-21
oh... duh.

it's in synaptic and works a treat under normal Breezy :)
(stopmotion 0.3.2-2)

---

### Post by tmckellar on 2005-12-26
Have you had any luck exporting to a video file? I'm having a horrible time trying to get the mencoder plugin to work.

Just thought I'd throw a few other ideas in here for ya too (I'm a stopmotion guy myself). For adding sound and stuff I'd give kino a whirl. Also in the repositories. If you want to use some more in-depth stuff I'd give Jahshaka a try. [http://sourceforge.net/projects/jahshakafx](http://sourceforge.net/projects/jahshakafx) [http://www.jahshaka.org/](http://www.jahshaka.org/) They have an Ubuntu .run file at the sourceforge page. Unfortunately I haven't been able to get it to work but I believe it may have something to do with the problem I'm having with exporting video in stopmotion.

And on a side note. If you come across a program for stop-motion animation called Myrtille, DO NOT, I repeat DO NOT ATTEMPT TO INSTALL THE .DEB FILE. If anything I'd try using alien on an rpm. But unless you have a lot of free time to kill while you reinstall Ubuntu because you can't get rid of it I wouldn't even consider it.

---

### Post by bjoernen on 2006-01-13
Mencoder is kind of tricky to use in some circumstances. On the other side it is nice when it works :-) To those of you having trouble with video export in stopmotion, I suggest you to try the following command (inside stopmotion):

mencoder -ovc lavc -lavcopts vcodec=msmpeg4v2:vpass=1:$opt -mf type=jpg:fps=8 -o $VIDEOFILE mf://$IMAGEPATH/*.jpg

This is a default option in the latest release (0.3.3) which is available on ubuntu soon. Go to the projects website and grab the latest release if you can't wait :-) [http://stopmotion.bjoernen.com](http://stopmotion.bjoernen.com)

---

### Post by bjoernen on 2006-01-13
Another option, using ffmpeg: 

ffmpeg -r 10 -b 1800 -i $IMAGEPATH/%06d.jpg $VIDEOFILE

---

### Post by bloodyserb on 2006-07-08
I tried replacing the "Start Encoder:" line for mencoder mpeg4 in export with the one you gave above,"mencoder -ovc lavc -lavcopts vcodec=msmpeg4v2:vpass=1:$opt -mf type=jpg:fps=8 -o$VIDEOFILE mf://$IMAGEPATH/*.jpg" and got the same error: "Video export failed.  Please check your settings in the preference menu."  What am I doing wrong?

---

### Post by Herbt on 2006-07-27
The stopmotion defaults never worked for me either. I sorted this one out using mjpeg that I ran from the command line. No sound though. 

```
mencoder mf://*.jpg -mf w=854:h=480:fps=4:type=jpg -ovc lavc -lavcopts vcodec=mjpeg -o thursday.avi
```

---

### Post by Spainface on 2006-08-19
My problem with stopmotion is that I can't get it to recognize any of my images.  On the command line it comes up:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Unsupported call to FAMSuspendMonitor()
/bin/cp: target `/home/one/.stopmotion/tmp/tmp_0.JPG' is not a directory

AND:

QImage::scale: Image is a null image
Unsupported call to FAMResumeMonitor()


I've been trying to add images from my desktop in .jpg format.

Any thoughts?

---

### Post by harderthanjss on 2006-08-22
I've been having the same problem.

---

### Post by familyaj on 2006-12-05
firstly, stopmotion doesnt seem to recognise either directories or files which have a space (even if preceeded by a backward slash). secondly, the tmp  files in .stopmotion ,and the tmp directory, seem to be owned by root -i am still struggling with the same issues myself- good luck!

---

### Post by kickabear on 2007-06-01
Stopmotion is a great program.  I spliced together a bunch of jpeg files in about 10 minutes last night.  The preview looked amazing.  Then I tried to export video and I wanted to cry...

I spent over an hour beating my head on the keyboard.  I tried all 4 of the default encoder settings (Feisty) but all of them produced errors.

Error 1: No encoder installed.  Used Synaptic to install ffmpeg and mencoder.
Error 2: mencoder reported truncated input.  WTF?  
Error 3: ffmpeg reported that the format was not recognized.  Seriously, WTF?

For 2 and 3, the problem was that my digital camera uses an extension of JPG, while the command strings in stopmotion used an extension of jpg.  I switched the encoder extension to uppercase, and suddenly, I have output.  I tried avi and mp4 with ffmpeg and mencoder defaults to avi.  

Error 4: When using ffmpeg, I kept getting an "unrecognized" output format.  For ffmpeg, in the Export File dialog, you have to give your output filename an extension.  Whatever extension you give is the format of the video.  I. e., output_filename.avi produces an avi file, output_filename.mp4 produces an mpeg4 file, etc. 

Hope this helps someone!

---

### Post by variona on 2007-07-24
After some experimenting, I got stopmotion working with my DV-Cam! 
stopmotion expects: ~/.stopmotion/capturedfile.jpg, but the default $IMAGEFILE leads wit dvgrab to ~/.stopmotion/capturedfile.jpg.jpg!
If you put into the commandline ~/.stopmotion/capturedfile as value for dvgrab's base parameter it actually works -until it crashes (at least on my system - i.e Ubuntustudio - making it necessary to trash the .stopmotion directory and copying a backup preferences.xml into the newly created .stopmotion directory. As for the crashes - save often save early and put your project file somewhere outside the .stopmotion dir. 
HTH
variona

---

### Post by simurg56 on 2008-06-03
Hi, I am using ubuntu 7.10,
stopmotion didn't work for me too, it didn't export any video. But when I installed 'mencoder 386' with synaptic , it worked fine. Now I can export the video. the solution may be that...

---

