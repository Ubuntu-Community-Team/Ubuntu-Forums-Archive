---
title: "K3b and FFMepg error - from source"
date: 2005-07-23
forum: General Help
---

### Post by michellembrodeur on 2005-07-23
Has anyone got K3B installed from source files.
I got FFMpeg install from source
Transcode installed from source
MPlayer installed from source
everything everyone ever says you need and all the stuff at K3B.org says you need or optional. their all installed.
But when Installing K3B I get the error from k3bffmpegwrapper.cpp 

here it is.
"if /bin/sh ../../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../../..  -I./../../../libk3b/core -I./../../../libk3b/plugin -I./../../../libk3bdevice -I/usr/include/kde -I/usr/share/qt3/include -I/usr/X11R6/include  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wno-non-virtual-dtor -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT k3bffmpegwrapper.lo -MD -MP -MF ".deps/k3bffmpegwrapper.Tpo" \
  -c -o k3bffmpegwrapper.lo `test -f 'k3bffmpegwrapper.cpp' || echo './'`k3bffmpegwrapper.cpp; \
then mv -f ".deps/k3bffmpegwrapper.Tpo" ".deps/k3bffmpegwrapper.Plo"; \
else rm -f ".deps/k3bffmpegwrapper.Tpo"; exit 1; \
fi
k3bffmpegwrapper.cpp: In member function `bool K3bFFMpegFile::open()':
k3bffmpegwrapper.cpp:85: error: cannot convert `AVCodecContext**' to `
   AVCodecContext*' in initialization
k3bffmpegwrapper.cpp: In member function `void K3bFFMpegFile::close()':
k3bffmpegwrapper.cpp:127: error: cannot convert `AVCodecContext**' to `
   AVCodecContext*' for argument `1' to `int avcodec_close(AVCodecContext*)'
k3bffmpegwrapper.cpp: In member function `int K3bFFMpegFile::sampleRate() const
   ':
k3bffmpegwrapper.cpp:146: error: request for member `sample_rate' in `
   this->K3bFFMpegFile::d->K3bFFMpegFile::Private::formatContext->AVFormatContext::streams[0]->AVStream::codec
   ', which is of non-class type `AVCodecContext*'
k3bffmpegwrapper.cpp: In member function `int K3bFFMpegFile::channels() const':
k3bffmpegwrapper.cpp:152: error: request for member `channels' in `
   this->K3bFFMpegFile::d->K3bFFMpegFile::Private::formatContext->AVFormatContext::streams[0]->AVStream::codec
   ', which is of non-class type `AVCodecContext*'
k3bffmpegwrapper.cpp: In member function `int K3bFFMpegFile::type() const':
k3bffmpegwrapper.cpp:158: error: request for member `codec_id' in `
   this->K3bFFMpegFile::d->K3bFFMpegFile::Private::formatContext->AVFormatContext::streams[0]->AVStream::codec
   ', which is of non-class type `AVCodecContext*'
k3bffmpegwrapper.cpp: In member function `QString K3bFFMpegFile::typeComment()
   const':
k3bffmpegwrapper.cpp:164: error: request for member `codec_id' in `
   this->K3bFFMpegFile::d->K3bFFMpegFile::Private::formatContext->AVFormatContext::streams[0]->AVStream::codec
   ', which is of non-class type `AVCodecContext*'
k3bffmpegwrapper.cpp: In member function `int K3bFFMpegFile::fillOutputBuffer()
   ':
k3bffmpegwrapper.cpp:262: error: cannot convert `AVCodecContext**' to `
   AVCodecContext*' for argument `1' to `int
   avcodec_decode_audio(AVCodecContext*, int16_t*, int*, uint8_t*, int)'
make[4]: *** [k3bffmpegwrapper.lo] Error 1
make[4]: Leaving directory `/root/k3b-0.12.2/plugins/decoder/ffmpeg'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/k3b-0.12.2/plugins/decoder'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/k3b-0.12.2/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/k3b-0.12.2'
make: *** [all] Error 2
root@krynn:~/k3b-0.12.2 #
"

everything compiles but that.

But I have a fresh install of ffmpeg. what is the problem if anyone know.

thanks in advance
Michelle Brodeur

---

