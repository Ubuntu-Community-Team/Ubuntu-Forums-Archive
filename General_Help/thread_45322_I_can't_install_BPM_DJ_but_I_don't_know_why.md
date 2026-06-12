---
title: "I can't install BPM DJ but I don't know why"
date: 2005-06-29
forum: General Help
---

### Post by Ferio on 2005-06-29
Hello, I wanted to install this program:

[http://bpmdj.sourceforge.net/aftersplash.html]("http://bpmdj.sourceforge.net/aftersplash.html")

So I download the source files, but when I do ./configure, it says it needs some distro-dependant file; I've tried to use the included Debian one, but I don't know how, and I haven't found any file in which this matter was covered. Has anyone by chance tried to install this programme?

And another question: is there any other known programme to count the BPMs of a .mp3 file? That's the reason why I want to install it, but if there is an easiest way, I will give this up.

PS: there's a .bin download, but I'm not sure that I could use alien to mutate the files, and I don't know hot to do it, anyway, since I haven't ever done it.

---

### Post by Xian on 2005-06-29
[QUOTE=Ferio]So I download the source files, but when I do ./configure, it says it needs some distro-dependant file; I've tried to use the included Debian one, but I don't know how, and I haven't found any file in which this matter was covered.[/QUOTE]
It would be helpful if you would post the actual error message.

In addition, make sure you follow the [Set-Up](http://bpmdj.sourceforge.net/setup.html) instructions by checking that you have all the recommended pacakges installed before attempting the configure session.

---

### Post by Ferio on 2005-06-30
Yeah, I thought about posting the error afterwards, I'll do it as soon as I get home tonight, and I'll make sure I've got the packages (I didn't notice it had dependencies :???:). Thank you!

---

### Post by Ferio on 2005-06-30
OK, so the first step I must follow is:

"To compile the software you need certain development tools. These are
    [indent]the linux soundcard headers, either the OSS headers or the ALSA headers or both.
     If you plan to use the ALSA driver, you will need alsalib
     gcc
     <li>qt-designer (called designer),
         qt header files
     qt3.1
     fftw3.0"
   [/indent] But:

[list]
[*]I don't know which are the packages with the soundcard headers.   
[*]There's a packet called "qt3-designer", is this the "qt-designer"?   
[*]I don't know which are the packages with the qt header files.   
[*]It seems that the version of qt included with Ubuntu is 3.0, but it needs 3.1.   
[*]And the version of fftw included is 2, and it needs 3. 
[/list] Where could I get all these packages? :???:

---

### Post by mirwin77 on 2007-04-04
Guess I'm bringing this thread back from the dead.  I would like to install BPMDj [ (http://bpmdj.sourceforge.net)]("http://bpmdj.sourceforge.net/") but am having trouble with the instructions on the website.  Has anyone installed this on Ubuntu (or Kubuntu, thats what I'm currently using)?  Is BPMDj in a repository anywhere?  I'm looking for a program that will analyze an input to the sound card (in my case a turntable connected to the computer) rather then just scan a file so I can get a Beats Per Minute read out for a song currently playing on my turntable.  Any help on this is much appreaciated.

---

### Post by claypole on 2007-06-01
Once you have downloaded the tarball from sourceforge, untar it, cd into dir and create the file "defines" (see compile.txt) as follows:

CPP             = g++ -g -O0 -Wall -Wno-sign-compare
UIC             = uic
MOC             = moc
CFLAGS         += -D COMPILE_OSS -D COMPILE_ALSA -D COMPILE_JACK -D QT_THREAD_SUPPORT
LDFLAGS        += -lpthread -lm -lasound -lrt -lfftw3
QT_INCLUDE_PATH = -I/usr/include/qt3/
QT_LIBRARY_PATH =
QT_LIBS         = -lqt-mt

This is a version of the defines.debian that I edited to get to work.

Check the compile.txt file for dependancies as its clearer there than the website.  Install everything you need then run <make> and it should compile.

I then tried "make install" and get "make: *** No rule to make target `install'. Stop.".  I'm not sure why this is , so if anyone can help that would be great.  Ideally I would like to install using "checkinstall".

Anyway, you can then just run "./kbmp-dj" from the directory and it works.  You need to export the path of the directory where you compiled so kbpm-dj can access kbpm-play etc and create the ./music,./index and ./fragments directory.

Hope this helps.

---

