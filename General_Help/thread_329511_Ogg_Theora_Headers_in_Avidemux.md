---
title: "Ogg Theora Headers in Avidemux"
date: 2007-01-01
forum: General Help
---

### Post by kd7swh on 2007-01-01
Avidemux2 fails to open my ogg theora files.

Can anyone tell me how to clarify the file headers of an Ogg Theora file (OGM container)  so avidemux will open it? 

___

I have a freshly compiled copy of AviDemux 2.3 on edgy.

---

### Post by SadaraX on 2007-01-02
Theora is not supported in any version of Avidemux yet.


[http://www.avidemux.org/pun/viewtopic.php?id=1662#9](http://www.avidemux.org/pun/viewtopic.php?id=1662#9)

[quote=mean]
For theora, i need to figure out the header they use which is different from ogm
After that, it should be easy to add support for it as it is supported by libavcodec apparently
[/quote]

Sorry but unless you have some magic we do not know about you are out of luck for the moment. But if you actually do get it working, please let us know and we will see if we can apply a patch to the code.

---

### Post by kd7swh on 2007-01-02
Thanks, I ended up finding that thread after I made this post. mean and the others really have their hands full with all sorts of things for avidemux. It confuses me why theora support wouldn't be more portable seeing as how it is open source. I wonder if FFmpeg  or at least its libraries are really the answer though. 
FFmpeg does the ogg-theora > other codec conversion that I want but it produces artifacts and macro-vision type problems.   So I don't think it is a solid fix. Maybe Xiph can provide a solution.

---

### Post by JuanC on 2007-01-03
One person is trying to add Theora encoding into FFMPEG :

[http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2006-December/050289.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-devel/2006-December/050289.html)

Maybe if it get Theora encoding support into FFMPEG other projects like Avidemux would decode / encode Theora files.

---

