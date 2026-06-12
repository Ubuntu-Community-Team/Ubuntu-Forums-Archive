---
title: "Compiling ffmpeg with nvenc support"
date: 2015-02-15
forum: General Help
---

### Post by kirby2ig on 2015-02-15
Hello. I am trying to compie ffmpeg with nvenc support, which can be found here [https://github.com/Brainiarc7/ffmpeg_libnvenc](https://github.com/Brainiarc7/ffmpeg_libnvenc). When I try to configure it, it tells me that OpenCL is not installed. I am using an nVidia graphics card, so I figured that I should install nvidia-opencl-dev, but when I try to install it, it says: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 nvidia-opencl-dev : Depends: nvidia-libopencl1 (>= 319.37) but it is not installable or
                              nvidia-libopencl1-331 but it is not going to be installed or
                              nvidia-libopencl1-331-updates but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
How do I install OpenCL?

---

### Post by FakeOutdoorsman on 2015-02-16
FFmpeg has NVENC encoding support, so you don't need to use a dead fork, but the link you provided does have some [useful notes](https://github.com/Brainiarc7/ffmpeg_libnvenc#notes-on-building-on-linux):

> 
[list]
[*]Download and install the [NVIDIA NVENC SDK](https://developer.nvidia.com/nvidia-video-codec-sdk) for Windows (Yes, that is correct). Extract the SDK's content then navigate to "nvenc-xx.0/samples/nvEncoder/inc" and copy the header files therein to "/usr/include".
[*]Ensure that the NVIDIA CUDA SDK is installed, and copy "cuda.h" to "/usr/include".
[/list]

I recommend installing these files to "/usr/local/include" instead to follow Ubuntu's policy (IIRC) of not mixing user installed stuff with the system files/where official packages get installed.

You can then follow the [ffmpeg compile guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu), and add "--enable-nonfree --enable-nvenc" to your ffmpeg configure.

I don't have a supported graphics card, so I am unable to test now.

For OpenCL support I believe you need the package opencl-headers.

Your package installation issues are probably the result of a PPA-induced conflict, but that's not something I know much about.

---

### Post by kirby2ig on 2015-03-30
Don't mean to bump an old thread, but i ran into some problems with this. After compiling, i am getting the following when trying to record with nvenc:
```
ben@ben-MS-7887:~/bin$ ./ffmpeg -f x11grab -r 30 -s 1920x1080 -i :0.0 -vcodec nvenc -b:v 4500k ~/test.mkv
ffmpeg version 2.6.git Copyright (c) 2000-2015 the FFmpeg developers
  built with gcc 4.9.1 (Ubuntu 4.9.1-16ubuntu6)
  configuration: --prefix=/home/ben/ffmpeg_build --extra-cflags=-I/home/ben/ffmpeg_build/include --extra-ldflags=-L/home/ben/ffmpeg_build/lib --bindir=/home/ben/bin --enable-gpl --enable-libass --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-nvenc
  libavutil      54. 21.100 / 54. 21.100
  libavcodec     56. 32.100 / 56. 32.100
  libavformat    56. 26.101 / 56. 26.101
  libavdevice    56.  4.100 / 56.  4.100
  libavfilter     5. 13.101 /  5. 13.101
  libswscale      3.  1.101 /  3.  1.101
  libswresample   1.  1.100 /  1.  1.100
  libpostproc    53.  3.100 / 53.  3.100
Input #0, x11grab, from ':0.0':
  Duration: N/A, start: 1427760847.294773, bitrate: N/A
    Stream #0:0: Video: rawvideo (BGR[0] / 0x524742), bgr0, 1920x1080, 30 fps, 30 tbr, 1000k tbn, 30 tbc
[nvenc @ 0x34aeb60] >> dl_fn->cu_init(0) - failed with error code 0x3e7
Output #0, matroska, to '/home/ben/test.mkv':
    Stream #0:0: Video: h264, none, q=2-31, 128 kb/s, 30 fps
    Metadata:
      encoder         : Lavc56.32.100 nvenc
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo (native) -> h264 (nvenc))
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height


```

Here is the script that I used to compile ffmpeg.
[http://www.mediafire.com/view/oc79wc94dvr6xf9/ffmpeg_nvenc.sh](http://www.mediafire.com/view/oc79wc94dvr6xf9/ffmpeg_nvenc.sh)

---

### Post by FakeOutdoorsman on 2015-03-31
You'll probably have to ask the ffmpeg-user mailing list or the #ffmpeg IRC channel. There is someone in #ffmpeg who has FFmpeg nvenc coding experience, but I can't recall his nick and I have only been there once in the last 3 weeks.

---

### Post by kirby2ig on 2015-03-31
I ended up fixing this myself by installing the latest drivers from the nVidia website. There must have been a problem with the ones from the xedgers ppa.

---

### Post by FakeOutdoorsman on 2015-03-31
Oh, now that I think about it I remember [FFmpeg support for nvenc API before 5.0 was dropped](http://git.videolan.org/gitweb.cgi/ffmpeg.git/?a=commit;h=48f7c30bf793fcde604cc457225b7c93f87b3692) on March 24. This "raises the minimum required nvidia driver version to 347.09 on windows and 346.22 on linux".

This was done to support for H.265 encoding with nvenc, but without the extra conditional logic that would have been required to support <5.0 SDK due to the fact that the older and newer versions do not share common codec parameters.

---

