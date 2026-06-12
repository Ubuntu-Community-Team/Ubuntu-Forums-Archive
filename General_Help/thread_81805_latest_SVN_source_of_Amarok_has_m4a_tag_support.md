---
title: "latest SVN source of Amarok has m4a tag support"
date: 2005-10-25
forum: General Help
---

### Post by fangorious on 2005-10-25
The latest sources of Amarok in SVN have support for reading the tags of m4a audio files, so you can add them to your collection. Look here for info on building Amarok from SVN.

[http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn](http://ubuntuforums.org/showthread.php?t=80492&highlight=amarok+svn)

---

### Post by snooo on 2005-10-29
no.... no it doesnt.

Just followed the guide and my m4as were scanned as they were before, without meta info.

Hrm, ist ich doing something wrong?

---

### Post by snooo on 2005-10-30
found how to do it. m4a support is not supported by default and must be added manually.

When the script asks you whether you want any additional parameters passed to the configure script, add --with-mp4v2. Make sure that you have the dev files installed for both faad2 and mp4v2 as configure will not complain if it cant find them. It should then compile like a nice thing.

Dave

---

### Post by green_lifesaver on 2005-10-31
hmmm... did you mean to add the parameter as "add --with-mp4v2" or "--with-mp4v2". I just tried the last and still my m4a's are being treated as they were in the standard Ubuntu version from add applications. Thanks for the heads up though, I am really excited to get this working!

---

### Post by hansoffate on 2005-11-01
i went to check if i had faad2 and mp4v2.

I searched in synaptic manager and there was no listing of mp4v2.
I added "-with-mp4v2" when trying to compile it.  

```
# 9/10 - Compiling. (The time of this phase depends on the number of new source files that were downloaded.)
compiling /opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp
g++ -DHAVE_CONFIG_H -I./amarok/src/metadata/mp4 -I/opt/amarok-svn/amarok/src/metadata/mp4 -I. -I/usr/include/kde -I/usr/share/qt3/include -I. -I/usr/include -I/usr/local/include/taglib -DQT_THREAD_SUPPORT -D_REENTRANT -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -g3 -fno-inline -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common -DQT_CLEAN_NAMESPACE -DQT_NO_ASCII_CAST -DQT_NO_STL -DQT_NO_COMPAT -DQT_NO_TRANSLATION -fPIC -DPIC -c /opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp -o ./amarok/src/metadata/mp4/.libs/mp4properties.o -Wp,-MD,./amarok/src/metadata/mp4/.deps/mp4properties.TUlo
In file included from /opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:22:
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.h:31:17: error: mp4.h: No such file or directory
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.h:64: error: ‘MP4FileHandle’ has not been declared
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.h:68: error: ‘MP4FileHandle’ has not been declared
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.h:68: error: ‘MP4TrackId’ has not been declared
/opt/amarok-svn/amarok/src/metadata/mp4/mp4tag.h:46: error: ‘MP4FileHandle’ has not been declared
/opt/amarok-svn/amarok/src/metadata/mp4/taglib_mp4file.h:50: error: ‘MP4FileHandle’ has not been declared
/opt/amarok-svn/amarok/src/metadata/mp4/taglib_mp4file.h:86: error: ‘MP4FileHandle’ does not name a type
/opt/amarok-svn/amarok/src/metadata/mp4/taglib_mp4file.h:50: error: ‘MP4_INVALID_FILE_HANDLE’ was not declared in this scope
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:74: error: variable or field ‘readMP4Properties’ declared void
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:74: error: ‘int TagLib::MP4::Properties::readMP4Properties’ is not a static member of ‘class TagLib::MP4::Properties’
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:74: error: ‘MP4FileHandle’ was not declared in this scope
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:75: error: expected ‘,’ or ‘;’ before ‘{’ token
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:94: error: variable or field ‘readAudioTrackProperties’ declared void
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:94: error: ‘int TagLib::MP4::Properties::readAudioTrackProperties’ is not a static member of ‘class TagLib::MP4::Properties’
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:94: error: ‘MP4FileHandle’ was not declared in this scope
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:94: error: ‘MP4TrackId’ was not declared in this scope
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:94: error: initializer expression list treated as compound expression
/opt/amarok-svn/amarok/src/metadata/mp4/mp4properties.cpp:95: error: expected ‘,’ or ‘;’ before ‘{’ token
Error creating ./amarok/src/metadata/mp4/mp4properties.lo. Exit status 1.

```

I think it may be the fact that i don't have the mp4v2 files.  Where can I get them.

Thanks again,
Hans

---

### Post by green_lifesaver on 2005-11-01
All I had to do is search synaptic for mp4v2 and add all the files with the name in the title, I believe there were only two. Make sure that you have universe and multiverse enabled when you search, you can find out more here [www.ubuntuguide.org](www.ubuntuguide.org). I did that for both FAAD and mp4v2 and I had no problem with compile.

---

### Post by metwo on 2005-11-01
[QUOTE=hansoffate]I think it may be the fact that i don't have the mp4v2 files.  Where can I get them.[/QUOTE]

You need libmp4v2-0 and libmp4v2-dev, both are in the multiverse repository.

---

### Post by pickarooney on 2005-11-01
Amarok = worst program ever. I have only ever got it to function properly once in about 20 goes on different OSes and different machines (I'm more stubborn than is healthy)... and it still doesn't have ALSA support... what kind of rubbish program requires you to go fiddling about with all sort of device settings just to get an MP3 playing, and then skips like mental every time you open a new tab in your browser?

---

### Post by metwo on 2005-11-01
[QUOTE=pickarooney]Amarok = worst program ever. I have only ever got it to function properly once in about 20 goes on different OSes and different machines (I'm more stubborn than is healthy)... and it still doesn't have ALSA support... what kind of rubbish program requires you to go fiddling about with all sort of device settings just to get an MP3 playing, and then skips like mental every time you open a new tab in your browser?[/QUOTE]

The only time I've ever had problems is with the arts engine in the past, which always was pretty rubbish in amarok anyway. I've never had to touch any device settings either, I just chose the xine engine with the esd output plugin and away it went. Which setting did you have to play with?

And exactly how does it not support ALSA? mine plays back through ALSA just fine.

---

### Post by pickarooney on 2005-11-01
I may be using the wrong terms, but if I understand correctly there has never been direct ALSA support, everything passed through gstreamer/aRts/OSS.
That's my main gripe with it - unless you really know a fair bit about sound server thingummyjigs you won't get it to work. Every other music prog I've tried has worked out-of-the-box, but amaroK has always steadfastly refused to play the slightest note without at least a day's fiddling and a good knowledge of the technology behind it.

---

### Post by metwo on 2005-11-01
Have a look at this bit of the amarok FAQ:

[Can amarok output output direct to OSS/ALSA]("http://amarok.kde.org/amarokwiki/index.php/FAQ#Can_amaroK_output_directly_to_OSS.2FALSA.3F")

All you need to do to get it to play is choose an decoding engine (e.g. gstreamer) and choose an output (usually ALSA or esd).

---

### Post by green_lifesaver on 2005-11-01
Has anyone else actually been able to get Amarok reading AAC tags? Is there a special version of mp4v2 that is needed? I have it installed via synaptic and everything the program built fine except for no aac meta data?

---

### Post by metwo on 2005-11-02
[QUOTE=green_lifesaver]Has anyone else actually been able to get Amarok reading AAC tags? Is there a special version of mp4v2 that is needed? I have it installed via synaptic and everything the program built fine except for no aac meta data?[/QUOTE]

Works fine for me. make sure you have libmp4v2-dev from the multiverse repository, as well as libmp4v2 and you might need libfaad2, libfaad2-dev, faad and gstreamer-faad (not sure, but I've got them installed and they can't hurt!)

---

### Post by uopjohnson on 2005-11-09
I have tried this a couple of times and still no go.  I can play the file just fine if I open it directly, but it will not add itself to the collection.

---

### Post by TecnoVM64 on 2005-11-09
Whoa, The latest SVN version of amaroK is totally amazing, it's really stable, good-looking and it supports m4a/acc tag reading!, I think I'll keep using the SVN versions from now.

---

### Post by Manny C on 2005-11-09
[quote=uopjohnson]I have tried this a couple of times and still no go. I can play the file just fine if I open it directly, but it will not add itself to the collection.[/quote]

Same problem.

---

### Post by simoncullen on 2005-11-10
Same problem here, too.  I've recompiled it with the configure options, added in all of the libraries, but still no metadata with m4a files...

[QUOTE=Manny C]Same problem.[/QUOTE]

---

### Post by simoncullen on 2005-11-11
Same problem here, too.  If anyone has worked this out I'd be very happy to hear how.  Cheers!

[QUOTE=simoncullen]Same problem here, too.  I've recompiled it with the configure options, added in all of the libraries, but still no metadata with m4a files...[/QUOTE]

---

### Post by metwo on 2005-11-13
[QUOTE=simoncullen]Same problem here, too.  If anyone has worked this out I'd be very happy to hear how.  Cheers![/QUOTE]

The latest svn version displays which plugins are/aren't included after the ./configure, so if it doesn't say this is going to be included at this stage then you probably haven't got all the necessary libraries.

---

### Post by Manny C on 2005-11-13
[quote=metwo]The latest svn version displays which plugins are/aren't included after the ./configure, so if it doesn't say this is going to be included at this stage then you probably haven't got all the necessary libraries.[/quote]

I realise this. When running the get-amarok script, the compilation program advises me that I have compiled with m4a support. But two things are apparent:
[LIST=1]
[*]The tags for m4a files I have downloaded from iTunes using sharpmusique, aren't displayed correctly.   
[*]I can't edit the tags. [/LIST] Both problems suck bad.

---

### Post by daobear on 2005-11-29
Hi.  Can anyone tell me a url specificially where I can find a repository with the  mp4v2 libraries?
I've added multiverse at several:
[http://us.archive.ubuntu.com/ubuntu/dists/hoary](http://us.archive.ubuntu.com/ubuntu/dists/hoary)
[http://archive.ubuntu.com/ubuntu/dists/hoary](http://archive.ubuntu.com/ubuntu/dists/hoary)
[http://archive.ubuntu.com/ubuntu/dists/hoary-backports/](http://archive.ubuntu.com/ubuntu/dists/hoary-backports/)

But when I search for mp4v2 in synaptic, I get nothing.

---

