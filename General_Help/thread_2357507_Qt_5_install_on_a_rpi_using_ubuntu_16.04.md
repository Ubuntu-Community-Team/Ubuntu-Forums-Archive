---
title: "Qt 5 install on a rpi using ubuntu 16.04"
date: 2017-04-03
forum: General Help
---

### Post by bask185 on 2017-04-03
Hello,

I build a GUI app in Qt5 in windows. I need this app to run on a raspberry pi and I've been told that porting an app from windows -> raspberry pi is not very viable. So I said windows goodbye and installed ubuntu 16:04 (had a disk space issue so I could not have both OS at same time) with easy I installed latest Qt Creator, dropbox and I linked thunderbird mail to my work outlook mail thing. Than opened my application in Qt creator and it works like a charm, so than it was time to export the application to the rpi. Asking on the Qt forum I got pointed towards this tutorial
[PHP]https://wiki.qt.io/RaspberryPi_Beginners_Guide[/PHP]

It is a really bad tutorial... when I began I had no clue what I was precisely doing and why because the tutorial is not explaining a lot. After I finally understood what I was doing, I ran from one problem into another problem. 
1. I had to download something using wget, that results in corrupted downloads so you have to manually download the file from the link.
2. Had to download  ia32-libs  an out phased library, but luckily the tut. showed me replacements.. which were  not doing 'it' right. Stuffing my error in google leaded to the solution:  apt-get install lib32stdc++6 and this one did do the job (job was properly unzipping and installing a file)
3. Than I had to comile qtbase which.... worked but after ~1 million lines of code went by I saw a few lines which contained the words "error" and "failed" :( and we know how late it is then...   but hoping this would be normal I went on to the next step..

[HTML]sax/qxml.h:121:5: error: function ‘QXmlAttributes::QXmlAttributes(QXmlAttributes&&)’ defaulted on its first declaration with an exception-specification that differs from the implicit declaration ‘QXmlAttributes::QXmlAttributes(QXmlAttributes&&)’
Makefile:1477: recipe for target '.obj/qxml.o' failed
make[2]: *** [.obj/qxml.o] Error 1
make[2]: Leaving directory '/home/user/opt/qt5/qtbase/src/xml'
Makefile:294: recipe for target 'sub-xml-make_first' failed
make[1]: *** [sub-xml-make_first] Error 2
make[1]: Leaving directory '/home/user/opt/qt5/qtbase/src'
Makefile:46: recipe for target 'sub-src-make_first' failed
make: *** [sub-src-make_first] Error 2

[/HTML]

4.Now I had to compile other modules: 
[PHP]paulo@westeros:~/opt/qt5$ cd qtimageformats
paulo@westeros:~/opt/qt5/qtimageformats$ /usr/local/qt5pi/bin/qmake[/PHP]

and ofcourse the file/exe 'qmake' is not to be found in that folder. I did find an executable qmake somewhere else and I copied that one to my desired folder. But than.... : qmake: could not exec '/usr/lib/x86_64-linux-gnu/qt4/bin/qmake': No such file or directory.   Smart as I am :P I tried to use the folder in which I found this qmake exe but it gave the exact same error message.
5. after not doing the previous step, I still decided to burn the image with the DD (Destroy Data :) ) function on the sd card and it was corrupted

And from here I got stuck... total dead in the water..
Ofcourse not one soul on the Qt forum knows anything about it, there was one guy helping me but even he only knows so much ;)
Really great 'crossover' 'features' of Qt which are 'well explained' and documented on the 'up-to-date' Qt website....*sarcastic cough*....

I know it is a long shot but I wonder is somebody on this forum could help me out with this 'well documented and up-to-date super' tutorial. If I aint get this working I'll be forced to install the Qt Creator IDE on the rpi. And I doubt if it will run smooth...

---

### Post by bask185 on 2017-04-03
P.S. by manually downloading raspbian jessie I fixed the corrupted SD card issue

---

