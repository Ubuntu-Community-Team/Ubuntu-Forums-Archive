---
title: "[SOLVED] Unfamiliar with Java"
date: 2008-07-06
forum: General Help
---

### Post by dodle on 2008-07-06
I've been looking for a program to convert/encode some video files.  I want to try out one that I've found at [http://sourceforge.net]("http://sourceforge.net/projects/jmencode").  It came in a .jar file, and I have no clue how to execute/install/extract it.  Let me know if you have any info.

What video encoders/converters do you recommend?  I'm looking for one that converts from AVI to MPEG2.

Thanks

---

### Post by jespdj on 2008-07-06
First, make sure you have Java installed. Search for the package **sun-java6-jre** in Synaptic, or install it via a terminal command:
```
sudo apt-get install sun-java6-jre
```
Then, use the following command to run the program:
```
java -jar program.jar
```
There are a number of video and audio editing programs available for Ubuntu. One that you could use is Avidemux.

Instead of trying to find something on Internet, search in Synaptic first. Search for "video" (for example), and you'll find a list of programs that can do things with video.

---

### Post by dodle on 2008-07-06
Thanks a bunch, that worked great.  I didn't even realize that java wasn't installed.  There are so many applications with reference to java.  

I did search through synaptic but didn't think there was anything I was looking for.  I'll try out avidemux.  Thanks again.

---

### Post by dodle on 2008-07-06
I'm having a new problem.  I type in the command:```
java -jar (filename).jar
```A window pops up to run the program, but it is frozen and I end up having to kill the process.  Any ideas?

Also, thanks jespdj, Avidemux works well, except I haven't been able to figure out how to encode multiple files into one.  There is one that looks really interesting at sourceforge called [LiVES]("http://sourceforge.net/projects/lives/"), but I can't get it to work.  I've tried downloading and converting the .rpm with alien.  I think I'll try downloading the tarball.

---

### Post by jamesstansell on 2008-07-06
Two things.

1) the program may expect some options.  what project did the .jar file come from?

2) you likely have another Java virtual machine installed.  This should let you which one
```
$ java -version
```

Make the proprietary version from Sun the default:
```
$ sudo update-java-alternatives -s java-6-sun
```

---

### Post by dodle on 2008-07-06
Oh, thank you so much james.  That worked perfectly.  I like Java so much better now.  I am going to have a bunch of questions now.

---

### Post by dodle on 2008-07-08
I figured out that AviDemux has an option to append videos under the "file" menu.  So now I can convert multiple videos into one.  It's doing everything I want it to so far.  Thanks again.

In windows I was using VirtualDub Mpeg2 Mod, but it only encodes to AVI.

---

