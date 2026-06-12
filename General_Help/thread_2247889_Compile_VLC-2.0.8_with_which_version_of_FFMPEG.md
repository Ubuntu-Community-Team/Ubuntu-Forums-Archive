---
title: "Compile VLC-2.0.8 with which version of FFMPEG?"
date: 2014-10-11
forum: General Help
---

### Post by Max_Arthuro on 2014-10-11
Dear forum,

I would like to compile VLC version 2.0.8 (the last version to properly support subtitles after video cropping) but run into trouble with avio.c (error message see below). I guess I am using the wrong FFMPEG library version, does anyone know which one I should use? I tried with 1.2, 1.2.2 and the current version.

Thanks in advance!
Max

Error message after running ./compile:

```
 avio.c: At top level:ERROR   : avio.c:76: 5:  unknown type name 'URLContext'
     AVIOContext *context;
     ^
ERROR   : avio.c:80: 5:  unknown type name 'URLContext'
     AVIOContext *context;
     ^
WARNING : avio.c:86: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
avio.c: In function 'SetupAvioCb':
ERROR   : avio.c:103: 5:  implicit declaration of function 'url_set_interrupt_cb' [-Werror=implicit-function-declaration]
     url_set_interrupt_cb(access ? UrlInterruptCallbackSingle : NULL);
     ^
avio.c: In function 'OpenAvio':
ERROR   : avio.c:141: 5:  implicit declaration of function 'av_register_all' [-Werror=implicit-function-declaration]
     av_register_all();
     ^
WARNING : avio.c:145: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:146: 5:  implicit declaration of function 'url_open' [-Werror=implicit-function-declaration]
     ret = avio_open(&sys->context, url, AVIO_FLAG_READ);
     ^
ERROR   : avio.c:46: 25:  'URL_RDONLY' undeclared (first use in this function)
 # define AVIO_FLAG_READ URL_RDONLY
                         ^
avio.c:146:41: note: in expansion of macro 'AVIO_FLAG_READ'
     ret = avio_open(&sys->context, url, AVIO_FLAG_READ);
                                         ^
avio.c:46:25: note: each undeclared identifier is reported only once for each function it appears in
 # define AVIO_FLAG_READ URL_RDONLY
                         ^
avio.c:146:41: note: in expansion of macro 'AVIO_FLAG_READ'
     ret = avio_open(&sys->context, url, AVIO_FLAG_READ);
                                         ^
ERROR   : avio.c:155: 9:  'errno' undeclared (first use in this function)
         errno = AVUNERROR(ret);
         ^
ERROR   : avio.c:155: 9:  implicit declaration of function 'AVUNERROR' [-Werror=implicit-function-declaration]
WARNING : avio.c:162: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:166: 9:  implicit declaration of function 'url_close' [-Werror=implicit-function-declaration]
         avio_close(sys->context);
         ^
ERROR   : avio.c:171: 5:  implicit declaration of function 'url_filesize' [-Werror=implicit-function-declaration]
     int64_t size = avio_size(sys->context);
     ^
WARNING : avio.c:173: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:174: 29:  request for member 'is_streamed' in something not a structure or union
     seekable = !sys->context->is_streamed;
                             ^
avio.c: In function 'OutOpenAvio':
WARNING : avio.c:215: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:47: 26:  'URL_WRONLY' undeclared (first use in this function)
 # define AVIO_FLAG_WRITE URL_WRONLY
                          ^
avio.c:216:54: note: in expansion of macro 'AVIO_FLAG_WRITE'
     ret = avio_open(&sys->context, access->psz_path, AVIO_FLAG_WRITE);
                                                      ^
ERROR   : avio.c:226: 9:  'errno' undeclared (first use in this function)
         errno = AVUNERROR(ret);
         ^
WARNING : avio.c:231: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
avio.c: In function 'CloseAvio':
WARNING : avio.c:256: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
avio.c: In function 'OutCloseAvio':
WARNING : avio.c:269: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
avio.c: In function 'Read':
ERROR   : avio.c:279: 5:  implicit declaration of function 'url_read' [-Werror=implicit-function-declaration]
     int r = avio_read(access->p_sys->context, data, size);
     ^
avio.c: In function 'Write':
WARNING : avio.c:298: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:299: 9:  implicit declaration of function 'url_write' [-Werror=implicit-function-declaration]
         int written = url_write(p_sys->context, p_buffer->p_buffer, p_buffer->i_buffer);
         ^
ERROR   : avio.c:301: 13:  'errno' undeclared (first use in this function)
             errno = AVUNERROR(written);
             ^
avio.c: In function 'Seek':
ERROR   : avio.c:339: 9:  implicit declaration of function 'AVERROR' [-Werror=implicit-function-declaration]
         ret = AVERROR(EOVERFLOW);
         ^
ERROR   : avio.c:335: 20:  'EFBIG' undeclared (first use in this function)
 # define EOVERFLOW EFBIG
                    ^
avio.c:339:23: note: in expansion of macro 'EOVERFLOW'
         ret = AVERROR(EOVERFLOW);
                       ^
ERROR   : avio.c:341: 9:  implicit declaration of function 'url_seek' [-Werror=implicit-function-declaration]
         ret = avio_seek(sys->context, position, SEEK_SET);
         ^
ERROR   : avio.c:343: 9:  'errno' undeclared (first use in this function)
         errno = AVUNERROR(ret);
         ^
avio.c: In function 'Control':
WARNING : avio.c:390: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:391: 27:  request for member 'is_streamed' in something not a structure or union
         *b = !sys->context->is_streamed;
                           ^
WARNING : avio.c:398: 5:  "LIBAVFORMAT_VERSION_MAJOR" is not defined [-Wundef]
 #if LIBAVFORMAT_VERSION_MAJOR < 54
     ^
ERROR   : avio.c:399: 26:  request for member 'prot' in something not a structure or union
         *b = sys->context->prot->url_read_pause != NULL;
                          ^
ERROR   : avio.c:415: 9:  implicit declaration of function 'av_url_read_pause' [-Werror=implicit-function-declaration]
         if (avio_pause(sys->context, is_paused)< 0)
         ^
cc1: some warnings being treated as errors
make: *** [all] Error 2



```

---

### Post by kc1di on 2014-10-11
Hi Max_Arthuro  and welcome to Ubuntu,

Version 2.08 is an older version. Which release of Ubuntu are you using?
the latest version of VLC is 2.1.5 and 2.1.4 is in the 14.04.1 repository and can be installed from there.
vlc-2.1.5 can be downloaded already built for ubuntu 13.10 and It will most likely also work for 14.04. 
So Actually your probly trying to build 2.08 on to a too new  ffmpeg.

---

### Post by Max_Arthuro on 2014-10-11
Hi kc1di

The thing is: all versions after 2.0.8 have the bug that when I crop a movie to 16:9, the subtitles are in the middle of the screen. That's why I'd like to run 2.0.8, which is the latest version without that bug.

Is there a way to obtain it? All I found was the source.

Best
Max

---

### Post by kc1di on 2014-10-11
you can get it [from here]("http://packages.ubuntu.com/precise/i386/vlc/download"), but not sure you'll get all the dependencies needed.  
give it a try though.

---

### Post by nerdtron on 2014-10-11
Not really relevant, but I think you might want to give SMPlayer a try?. It's not very pretty on the default GUI (although you can have themes). It has lots of options and keyboard shortcuts like VLC.

---

