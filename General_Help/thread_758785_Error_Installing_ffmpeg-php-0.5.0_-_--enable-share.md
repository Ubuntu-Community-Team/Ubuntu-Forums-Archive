---
title: "Error Installing ffmpeg-php-0.5.0 - --enable-shared option"
date: 2008-04-18
forum: General Help
---

### Post by mesach on 2008-04-18
I am trying to install FFmpeg, FFmpeg-PHP, Lame, Libogg, Libvorbis, FLVtool2, Mplayer, Mencoder, AMR Installation via the instructions at [http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation]("http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation")

Everything goes well except a few options, and since i'm a total Newb, I can't figure out where to fix it.

Ultimately i am getting hung up when installing ffmpeg-php-0.5.0 during the ./configure i get the following error

checking for ffmpeg support... yes, shared
checking for ffmpeg headers... configure: error: ffmpeg headers not found. Make sure you've built ffmpeg as shared libs using the --enable-shared option

now earlier during the ffmpeg installation i ran this command
./configure --enable-libmp3lame --enable-libogg --enable-libvorbis --disable-mmx --enable-shared --enable-amr-nb

it complained about --enable-libogg I searched and found someone else who had an issue with it and was advised to remove it so i did and it went on without complaining... or so I could tell.

Now as you can see i did enable-shared, so why is ffmpeg-php complaining about not having it shared?
Every post i have read doesn't seem to mention that they HAD enabled shared, it just looked like someone told them to enable it and they went back and re-./configured and it worked for them.

PLEASE HELP ME... I have already lost enough hair, i don't need to lose anymore...

---

### Post by mesach on 2008-04-18
SOLVED IT... here is what i found... cant remember how i found it though, but here it is for future generations who have this issue

[http://www.articlenet.org/view/printview-22.html](http://www.articlenet.org/view/printview-22.html)


Install ffMPEG-php

cd /usr/src/ffmpeg-php-0.5.0/
phpize
./configure && make && make install    

[B]Here you may get an error saying: 
"configure: error: ffmpeg headers not found. Make sure you've built ffmpeg as shared libs using the --enable-shared option" 

 (although you used the --enable-shared option above)    
[/B]

In this case, run first these commands:  

----------------------I had to change these to reflect the path i used /usr/local/src

 mkdir /usr/local/include/ffmpeg 
cp -p /usr/local/src/ffmpeg/libavformat/avio.h /usr/local/include/ffmpeg
cp -p /usr/local/src/ffmpeg/libavformat/avformat.h /usr/local/include/ffmpeg
cp -p /usr/local/src/ffmpeg/libavcodec/avcodec.h /usr/local/include/ffmpeg 

 Now run again the command:  
./configure && make && make install 
 It should work with no errors  Then continue the rest process with these commands     

 ln -s /usr/local/bin/ffmpeg /usr/bin/ffmpeg
 ln -s /usr/local/bin/mplayer /usr/bin/mplayer

---

