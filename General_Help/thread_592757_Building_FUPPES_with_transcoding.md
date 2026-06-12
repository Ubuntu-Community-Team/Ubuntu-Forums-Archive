---
title: "Building FUPPES with transcoding"
date: 2007-10-26
forum: General Help
---

### Post by b1mmer on 2007-10-26
Hello,

I am trying to compile FUPPES from SVN (10/04) with transcoding enabled under 7.10. I believe I have all the -dev packages and everything that required. ./configure --enable-video-transcoding works fine and shows following summary:

```

  SUMMARY

  audio transcoding enabled
    encoder:
      lame       : yes
      twolame    : no
      wav        : yes
      pcm        : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : no
      flac       : yes
      fadd       : no

  video transcoding (experimental)
  ffmpeg     : enabled


  iconv      : enabled
  uuid       : disabled
  taglib     : disabled
  ImageMagick: disabled
  libavformat: enabled

GNOME
  panel applet : disabled
  libnotify    : disabled

Thanks for using fuppes
please report bugs

```

however make gives me following error:

```

 g++ -DHAVE_CONFIG_H -I. -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/include/swscale -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT TranscodingMgr.lo -MD -MP -MF .deps/TranscodingMgr.Tpo -c lib/Transcoding/TranscodingMgr.cpp  -fPIC -DPIC -o .libs/TranscodingMgr.o
In file included from lib/Transcoding/FFmpegWrapper.h:37,
                 from lib/Transcoding/TranscodingMgr.cpp:64:
lib/Transcoding/ffmpeg/ffmpeg.h:47:19: error: mem.h: No such file or directory

```

I did some research on mem.h and it seems like mem.h should be part of libav development package (or ffmpeg-dev) but libav-dev and ffmpeg-dev in 7.10 do not include mem.h. SVN verison of ffmpeg does have mem.h but it looks like I should rebuild whole ffmpeg (with probably all the dependencies) in order to make everything work which I really try to avoid. 

Has anyone tried to build FUPPES under 7.10 with --enable-video-transcoding? I could use some tips.

thank you.

---

### Post by b1mmer on 2007-10-27
/bump

---

### Post by artzxp on 2007-11-01
[http://anonymouscoward.org/art/streaming-and-transcoding-fly-xbox-360/](http://anonymouscoward.org/art/streaming-and-transcoding-fly-xbox-360/)

just follow the instructions exactly...
worked fine for me
good luck!

---

### Post by hebetude on 2007-11-03
```
./.libs/libfuppes.so: undefined reference to `av_strstart'
./.libs/libfuppes.so: undefined reference to `av_init_packet'
./.libs/libfuppes.so: undefined reference to `av_strlcpy'
collect2: ld returned 1 exit status
make[2]: *** [fuppes] Error 1
make[2]: Leaving directory `/home/drew/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/drew/fuppes/src'
make: *** [all-recursive] Error 1

```

This is the 4th unique exit status 1 I've found.  Fuppes is _not_ finished.

---

### Post by hebetude on 2007-11-19
just for kicks, so I feel special when I google these amazing error scenarios:
```

so -lX11 -lXfixes /usr/lib/libgmodule-2.0.so -ldl -ldbus-1 /usr/lib/libgobject-2.0.so /usr/lib/libglib-2.0.so ./.libs/libfuppes.so 
./.libs/libfuppes.so: undefined reference to `vorbis_analysis_headerout'
./.libs/libfuppes.so: undefined reference to `lame_set_out_samplerate'
./.libs/libfuppes.so: undefined reference to `lame_encode_buffer'
./.libs/libfuppes.so: undefined reference to `theora_encode_comment'
./.libs/libfuppes.so: undefined reference to `theora_info_clear'
./.libs/libfuppes.so: undefined reference to `lame_set_brate'
./.libs/libfuppes.so: undefined reference to `vorbis_analysis_blockout'
./.libs/libfuppes.so: undefined reference to `vorbis_info_clear'
./.libs/libfuppes.so: undefined reference to `vorbis_analysis_buffer'
./.libs/libfuppes.so: undefined reference to `lame_set_bWriteVbrTag'
./.libs/libfuppes.so: undefined reference to `theora_info_init'
./.libs/libfuppes.so: undefined reference to `vorbis_block_clear'
./.libs/libfuppes.so: undefined reference to `lame_close'
./.libs/libfuppes.so: undefined reference to `lame_set_VBR'
./.libs/libfuppes.so: undefined reference to `vorbis_analysis'
./.libs/libfuppes.so: undefined reference to `lame_get_framesize'
./.libs/libfuppes.so: undefined reference to `lame_init'
./.libs/libfuppes.so: undefined reference to `lame_set_quality'
./.libs/libfuppes.so: undefined reference to `vorbis_encode_setup_vbr'
./.libs/libfuppes.so: undefined reference to `lame_set_in_samplerate'
./.libs/libfuppes.so: undefined reference to `theora_comment_clear'
./.libs/libfuppes.so: undefined reference to `theora_encode_header'
./.libs/libfuppes.so: undefined reference to `lame_set_mode'
./.libs/libfuppes.so: undefined reference to `lame_set_num_channels'
./.libs/libfuppes.so: undefined reference to `vorbis_encode_setup_managed'
./.libs/libfuppes.so: undefined reference to `vorbis_encode_ctl'
./.libs/libfuppes.so: undefined reference to `vorbis_analysis_init'
./.libs/libfuppes.so: undefined reference to `vorbis_dsp_clear'
./.libs/libfuppes.so: undefined reference to `vorbis_block_init'
./.libs/libfuppes.so: undefined reference to `theora_encode_packetout'
./.libs/libfuppes.so: undefined reference to `theora_encode_tables'
./.libs/libfuppes.so: undefined reference to `lame_encode_flush'
./.libs/libfuppes.so: undefined reference to `lame_encode_buffer_interleaved'
./.libs/libfuppes.so: undefined reference to `vorbis_comment_init'
./.libs/libfuppes.so: undefined reference to `theora_clear'
./.libs/libfuppes.so: undefined reference to `vorbis_comment_clear'
./.libs/libfuppes.so: undefined reference to `lame_init_params'
./.libs/libfuppes.so: undefined reference to `theora_comment_init'
./.libs/libfuppes.so: undefined reference to `theora_encode_init'
./.libs/libfuppes.so: undefined reference to `vorbis_encode_setup_init'
./.libs/libfuppes.so: undefined reference to `vorbis_bitrate_addblock'
./.libs/libfuppes.so: undefined reference to `vorbis_comment_add_tag'
./.libs/libfuppes.so: undefined reference to `theora_encode_YUVin'
./.libs/libfuppes.so: undefined reference to `vorbis_bitrate_flushpacket'
./.libs/libfuppes.so: undefined reference to `vorbis_analysis_wrote'
./.libs/libfuppes.so: undefined reference to `lame_set_VBR_q'
./.libs/libfuppes.so: undefined reference to `vorbis_info_init'
collect2: ld returned 1 exit status
make[2]: *** [fuppes] Error 1

```

FFmpeg v. 11067
Fuppes v 551


Following the explicit instructions on fuppes website

---

### Post by hebetude on 2007-11-26
So, I've solved this problem.  The guy making the "ubuntu" guide is wrong in his ffmpeg parameters.  Here's the settings that worked for me

```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads \
--enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm \
--enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 \
--enable-libxvid --enable-shared --enable-pp --enable-pthreads

```ffmpeg 11093
fuppes 541? latest on 11/26

---

### Post by chiabre on 2007-11-27
tried this..

> **hebetude said:**
> 

```
./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads \
--enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm \
--enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 \
--enable-libxvid --enable-shared --enable-pp --enable-pthreads

```

but no way...


```


...
lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_audio_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:2060: warning: converting to 'int' from 'float'
make[2]: *** [ffmpeg.lo] Error 1
make[2]: Leaving directory `$/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `$fuppes/src'
make: *** [all-recursive] Error 1


```


any ideas to solve?

ubu 7.10
ffmpeg 11097
fuppes 571

---

### Post by hebetude on 2007-11-27
your stuff is old already ;)
```
Checked out revision 11107.

```

You're paying the price of bleeding edge there, that looks like a coding error that got put into ffmpeg "release".

---

### Post by miaviator278 on 2007-11-28
**[COLOR="Blue"]HOW TO INSTALL FUPPES WITH TRANSCODING ON 7.10[/COLOR]**

THANK YOU to [COLOR="Red"]**hebetude**[/COLOR] for documenting version numbers!!!!!!!!!!!!!!!!!


```
sudo apt-get build-dep ffmpeg
sudo apt-get install libdc1394-13-dev libgsm1-dev libimlib2-dev libraw1394-dev libsdl1.2-dev texi2html autoconf automake1.9 libtool
libpcre3-dev libxml2-dev libsqlite3-dev uuid-dev libtag1-dev liblame-dev libflac-dev libmpcdec-dev libfaac-dev libfaad2-dev liba52-0
.7.4-dev libxvidcore4-dev libx264-dev subversion checkinstall libnotify-dev libpanel-applet2-dev twolame* libpanel-applet2-dev libto
ol libx264-dev libxvidcore4-dev m4 uuid-dev liba52-0.7.4-dev libfaac-dev libfaad2-0 libfaad2-dev liblame-dev libmp4v2-dev libmpcdec-
dev libnotify-dev

sudo chown :users /usr/src
cd /usr/src
svn checkout -r 11093 svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/

./configure --prefix=/usr --enable-gpl --enable-pp \
--enable-pthreads --enable-liba52 --enable-libdc1394 \
--enable-libfaac --enable-libfaad --enable-libgsm \
--enable-libmp3lame --enable-libtheora \
--enable-libvorbis --enable-libx264 --enable-libxvid \
--disable-debug
make
sudo checkinstall
cd ..

svn co -r 541 http://fuppes-svn.ulrich-voelkel.de/trunk fuppes
cd fuppes/
autoreconf -vfi
./configure --prefix=/usr --disable-imagemagick \
--enable-video-transcoding \
--enable-gnome-panel-applet --enable-libnotify
make

sudo checkinstall

echo ENJOY I have no idea how to use this program.
```

---

### Post by hebetude on 2007-11-28
As far as usage, yay they have poor documentation.  From what I could tell "fuppes" is a sort of client (all it does is popup windows when it finds a uPNP server) and fuppesd is the server side of things.  You will be able to access some not all features via the web interface which is determined by your config file.

The config file is stored at ~/.fuppes/fuppes.cfg.  The file listings (when you add files via the web interface) is stored at ~/.fuppes/fuppes.db.  Another important file is vfolder.cfg, I don't know how to use that yet.  There are some scripts written for fuppes thanks to their wiki.  However, they are a bit buggy.  

Just a FYI, I couldn't get anything to play on my PS3.  I couldn't even get fuppes to share my mp3 files which requires no transcoding.  It did list my avi files, but failed to transcode them into a format the PS3 can read.  I'm seriously dome with this software, it's just another generic project by some guy with dubious intentions for its usability.

If you need a uPnP server, check out mediatomb.  It's in the repository, comes with scripts that work and I detailed some stuff on these forums for how to get it working with PS3 1.80-2.01.

Good luck

---

### Post by miaviator278 on 2007-11-29
I agree that fuppes is not what i wanted,  although people said it was.   I did't like media tomb so much, so far i've heard tversity and orb for windows will work but that's not worthwhile.

---

### Post by hebetude on 2007-11-29
Mediatomb works pretty well, as long as you're willing to spend some time transcoding to a format the PS3 can read.  It even allows you to skip through the movie which is nice and the bluetooth controller has about 10x the range of my wireless keyboard.  Although HD content takes me about 8hrs to transcode and comes out with significantly lower quality.

---

### Post by chiabre on 2007-11-29
> **hebetude said:**
> your stuff is old already ;)
```
Checked out revision 11107.

```

You're paying the price of bleeding edge there, that looks like a coding error that got put into ffmpeg "release".

No m8...i also tried this (with fix snv version number)

> **miaviator278 said:**
> **[COLOR="Blue"]HOW TO INSTALL FUPPES WITH TRANSCODING ON 7.10[/COLOR]**

THANK YOU to [COLOR="Red"]**hebetude**[/COLOR] for documenting version numbers!!!!!!!!!!!!!!!!!


```
sudo apt-get build-dep ffmpeg
sudo apt-get install libdc1394-13-dev libgsm1-dev libimlib2-dev libraw1394-dev libsdl1.2-dev texi2html autoconf automake1.9 libtool
libpcre3-dev libxml2-dev libsqlite3-dev uuid-dev libtag1-dev liblame-dev libflac-dev libmpcdec-dev libfaac-dev libfaad2-dev liba52-0
.7.4-dev libxvidcore4-dev libx264-dev subversion checkinstall libnotify-dev libpanel-applet2-dev twolame* libpanel-applet2-dev libto
ol libx264-dev libxvidcore4-dev m4 uuid-dev liba52-0.7.4-dev libfaac-dev libfaad2-0 libfaad2-dev liblame-dev libmp4v2-dev libmpcdec-
dev libnotify-dev

sudo chown :users /usr/src
cd /usr/src
svn checkout -r 11093 svn://svn.mplayerhq.hu/ffmpeg/trunk ffmpeg
cd ffmpeg/

./configure --prefix=/usr --enable-gpl --enable-pp \
--enable-pthreads --enable-liba52 --enable-libdc1394 \
--enable-libfaac --enable-libfaad --enable-libgsm \
--enable-libmp3lame --enable-libtheora \
--enable-libvorbis --enable-libx264 --enable-libxvid \
--disable-debug
make
sudo checkinstall
cd ..

svn co -r 541 http://fuppes-svn.ulrich-voelkel.de/trunk fuppes
cd fuppes/
autoreconf -vfi
./configure --prefix=/usr --disable-imagemagick \
--enable-video-transcoding \
--enable-gnome-panel-applet --enable-libnotify
make

sudo checkinstall

echo ENJOY I have no idea how to use this program.
```


..but same error during "make"

```


lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_video_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:1943: warning: converting to 'int' from 'float'
lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_audio_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:2053: warning: converting to 'int' from 'float'
make[2]: *** [ffmpeg.lo] Error 1
make[2]: Leaving directory `/usr/src/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/fuppes/src'
make: *** [all-recursive] Error 1



```


:(

---

### Post by soniclava on 2007-12-05
I also get the same error during the make... 

> lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_video_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:1943: warning: converting to 'int' from 'float'
lib/Transcoding/ffmpeg/ffmpeg.cpp: In member function 'void CFFmpeg::new_audio_stream(AVFormatContext*)':
lib/Transcoding/ffmpeg/ffmpeg.cpp:2053: warning: converting to 'int' from 'float'
make[2]: *** [ffmpeg.lo] Error 1
make[2]: Leaving directory `/usr/src/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/fuppes/src'
make: *** [all-recursive] Error 1

Any advice would help.  Thanks.

---

### Post by hebetude on 2007-12-05
You two guys try with the parameters I passed, I noticed you were using a slightly different set of parameters.  Are you compiling in 64bit? and which version of Ubuntu are you using?

```

./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads \ 
--enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm \ 
--enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 \ 
--enable-libxvid --enable-shared

```

---

### Post by Egalfire on 2007-12-05
hey i am getting this error on gutsy 64 bit:

michael@michael-desktop:~/fuppes$ make
Making all in src
make[1]: Entering directory `/home/michael/fuppes/src'
make  all-am
make[2]: Entering directory `/home/michael/fuppes/src'
/bin/bash ../libtool --tag=CXX   --mode=compile g++ -DHAVE_CONFIG_H -I. -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg    -I/usr/local/include -I/usr/include/ffmpeg   -I/usr/include/libxml2       -D_FILE_OFFSET_BITS=64    -g -O2 -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c -o FileDetails.lo `test -f 'lib/ContentDirectory/FileDetails.cpp' || echo './'`lib/ContentDirectory/FileDetails.cpp
 g++ -DHAVE_CONFIG_H -I. -D__STDC_CONSTANT_MACROS -I/usr/include/ffmpeg -I/usr/local/include -I/usr/include/ffmpeg -I/usr/include/libxml2 -D_FILE_OFFSET_BITS=64 -g -O2 -MT FileDetails.lo -MD -MP -MF .deps/FileDetails.Tpo -c lib/ContentDirectory/FileDetails.cpp  -fPIC -DPIC -o .libs/FileDetails.o
/usr/local/include/dlna.h:155: error: expected identifier before ';' token
/usr/local/include/dlna.h:155: error: multiple types in one declaration
/usr/local/include/dlna.h:155: error: declaration does not declare anything
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute ignored in declaration of 'struct ImgReSampleContext'
/usr/include/ffmpeg/avcodec.h:2432: warning: attribute for 'struct ImgReSampleContext' must follow the 'struct' keyword
/usr/include/ffmpeg/avcodec.h:2437: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2444: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2448: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avcodec.h:2450: warning: 'ImgReSampleContext' is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2434)
/usr/include/ffmpeg/avformat.h:282: warning: 'AVFrac' is deprecated (declared at /usr/include/ffmpeg/avformat.h:118)
lib/ContentDirectory/FileDetails.cpp: In member function 'std::string CFileDetails::GetDLNAString(std::string)':
lib/ContentDirectory/FileDetails.cpp:446: error: invalid conversion from 'int' to 'dlna_org_flags_t'
lib/ContentDirectory/FileDetails.cpp:448: error: 'dlna' was not declared in this scope
make[2]: *** [FileDetails.lo] Error 1
make[2]: Leaving directory `/home/michael/fuppes/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/michael/fuppes/src'
make: *** [all-recursive] Error 1

any help would be greatly appreciated thanx in advance

---

### Post by hebetude on 2007-12-05
post your ./configure parameters please

---

### Post by Egalfire on 2007-12-06
> **hebetude said:**
> post your ./configure parameters please

./configure --enable-video-transcoding

---

### Post by hebetude on 2007-12-06
use this:
If you don't want to install the various dependencies, just remove them.  It will tell you if any dependency can't be found.
```

./configure --prefix=/usr --enable-gpl --enable-pp --enable-pthreads \ 
--enable-liba52 --enable-libdc1394 --enable-libfaac --enable-libfaad --enable-libgsm \ 
--enable-libmp3lame --enable-libtheora --enable-libvorbis --enable-libx264 \ 
--enable-libxvid --enable-shared
```

---

### Post by Tadhg on 2007-12-08
I think there's a problem with the libdlna headers

[http://sourceforge.net/forum/forum.php?thread_id=1886911&forum_id=475749](http://sourceforge.net/forum/forum.php?thread_id=1886911&forum_id=475749)

I'm getting the same errors, after a clean reinstall of gutsy.

---

### Post by Anubis on 2007-12-17
[http://sourceforge.net/forum/message.php?msg_id=4672657]("http://sourceforge.net/forum/message.php?msg_id=4672657")

> RE: problem compiling when I enable transcodi (New)
By: hijstr (hijstr) - 2007-12-12 15:07
excellent! I've got it installed now. THere was one hiccup along the way though, and I needed to add  
 
std::string GetDLNAString(std::string); 
 
into the FileDetails.h in the CFileDetails class declaration. After that everything compiled 
 
Thanks! 

I was able to finally successfully get past the "make" step by editing the above file to include that line. However now, fuppes compiles with transcoding disabled?

SUMMARY

  audio transcoding enabled
    encoder:
      lame       : yes
      twolame    : no
      wav        : yes
      pcm        : yes
    decoder:
      vorbis     : yes (libvorbisfile)
      mpc        : yes
      flac       : yes
      faad       : yes (aac/mp4)

  video transcoding (experimental)
  ffmpeg     : disabled


  iconv      : enabled
  uuid       : enabled
  libdlna    : disabled
  taglib     : enabled
  ImageMagick: disabled
  simage     : disabled
  libavformat: disabled

GNOME
  panel applet : disabled
  libnotify    : disabled

Thanks for using fuppes
please report bugs

---

### Post by hebetude on 2007-12-17
./configure --enable-transcoding

---

### Post by Anubis on 2007-12-19
> **hebetude said:**
> ./configure --enable-transcoding

That had nothing to do with it.

I got everything working now, except the gnome applet does not function.

FUPPES - SVN-r576
    the Free UPnP Entertainment Service
      [http://fuppes.ulrich-voelkel.de](http://fuppes.ulrich-voelkel.de)

webinterface: [http://192.168.1.100:32967](http://192.168.1.100:32967)

r = rebuild database
i = print system info
h = print help

press "ctrl-c" or "q" to quit

i
general information:
  version     : SVN-r576
  hostname    : xxx
  OS          : Linux 2.6.22-14-generic
  build at    : Dec 17 2007 13:40:11
  build with  : 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
  address     : 192.168.1.100
  sqlite      : 3.4.2
  log-level   : 1 (normal)
  webinterface: [http://192.168.1.100:32967/](http://192.168.1.100:32967/)

transcoding settings:
  lame    : enabled
  twolame : compiled without TwoLame support

active encoder: lame

  vorbis  : enabled
  musepack: enabled
  flac    : enabled


configuration file:

---

