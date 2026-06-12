---
title: "Convert MP2 video to MP3"
date: 2007-11-14
forum: General Help
---

### Post by knutschr on 2007-11-14
I want to convert a MP2 video to MP3 to be able to ude it at work on a Win machine.
(No new programs are allowed in it).

I search Synaptic for ' MP2 video converts' and installed iriverter, that is the program that showed up.

Trying to start iriverter gives:
> 
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
---
--- Settings:
---
---
!!! no swt-pi-gtk-3236 in java.library.path
!!!
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:823)
!!! java.lang.System.loadLibrary(System.java:1030)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!!
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)


I have reinstalled Java JRE with no luck.

Can anybody tell how I can proceed to do this convertion?

---

### Post by geirha on 2007-11-14
mp2 and mp3 are audio formats. (MPEG-1 Audio layer II and MPEG-1 Audio layer 3 respectively). So the application you have found is one that converts mp2 audio to mp3 audio. I'm guessing your video is in MPEG-2 format, and you want to convert it to what? You need to know what formats the windows machine can play. 

**mencoder** will convert between most formats, but it's a command line tool, and a bit hard to use if you have no previous experience with it. 

You might find some easy guides at [http://www.videohelp.com/](http://www.videohelp.com/) .

---

### Post by Jota37 on 2008-01-05
Hi, knutschr

I've just installed iriverter and faced the same problem. After some time searching, I found something that solved the problem for me -- although I haven't used iriverter extensively, since it does not really do what I expected anyway.

The solution (found [HERE]("https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/91237")) is to edit the file /usr/bin/iriverter (which is a shell script, just open it in Kate or some other editor) and change from:

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib -classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.
thestaticvoid.iriverter.ConverterUI $*
```

To:

```
java -Djava.library.path=$LD_LIBRARY_PATH:${exec_prefix}/lib**:/usr/lib/jni **-classpath $CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt.jar org.
thestaticvoid.iriverter.ConverterUI $*
```

Note the :/usr/lib/jni added there.

Another way to fix this is to add ```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/jni
``` to your /home/user/.bashrc file.

I hope this works for you.
Cheers
J

---

