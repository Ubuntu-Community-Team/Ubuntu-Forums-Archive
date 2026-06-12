---
title: "How to pull video from a Mini-DV camcorder???"
date: 2004-11-09
forum: General Help
---

### Post by oberon on 2004-11-09
I have only ever done this in windows and don't really know what needs to be done to do in in linux.  Is there something I need to configure the 1394 port?  Also, what apps would one use to compress/edit the video?  Thanks for your help.

---

### Post by jdong on 2004-11-09
enable the Universe repository (search the forum/ubuntu site), install kino, dvgrab, and mjpegtools.

Start Kino, and it'll have a nice interface to do everything from. You can get as far as creating a DVD-compatible MPEG file with Kino, then you'll have to use some other authoring solution (either command line dvd-author, or the Java based GUI called "Varsha" [varsha.sourceforge.net]) to burn it onto a DVD.


To use Varsha, you must have Java installed (again, search forum). Then, just go to the Varsha site, download the jar, then execute with **java varsha.jar**. Check Varsha settings, it has a list of programs that it needs to do its tasks. Have it "autodetect", then use Synaptic to install the missing tools.

---

### Post by oberon on 2004-11-10
Thanks for the info :)  I will give it a try.

---

