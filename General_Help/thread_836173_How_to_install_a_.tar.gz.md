---
title: "How to install a .tar.gz ?"
date: 2008-06-21
forum: General Help
---

### Post by The Pinny Parlour on 2008-06-21
Hello

Trying to install a program but I don't know how to.  It's a .tar.gz.  I have no idea how to install it.

Any help would be great.

TIA.

---

### Post by Christmas on 2008-06-21
What is the name of the program? If it's available in the repositories, you can try to install it directly using:

```
apt-get install program_name
```

It's probably a source code. Open your terminal, go to the directory where you saved it (e.g. *cd ~/Desktop*), then uncompress it:

```
tar -xzf compressed_file.tar.gz
```

Then change the working directory to the uncompressed directory and type:

```
./configure
make
sudo make install
```

If it has dependencies issues, search for them using *apt-cache search dependency* and install them with *apt-get install dependency*.

But, again, what program are you trying to install?

---

### Post by Jadd on 2008-06-21
Try to use .deb s in the future, they're much easier to install. Here's a link to [How to install anything in Ubuntu](http://monkeyblog.org/ubuntu/installing/).

---

### Post by The Pinny Parlour on 2008-06-21
Thanks for your help.  Unfortunately it doesn't work. Wish it was easier.  

keyHoleTV

---

### Post by Jadd on 2008-06-21
Which program are you trying to install?

---

### Post by bodhi.zazen on 2008-06-21
There are several tool to help with this.

This is my general advice :

[http://ubuntuforums.org/showpost.php?p=4473168&postcount=5](http://ubuntuforums.org/showpost.php?p=4473168&postcount=5)

---

### Post by Christmas on 2008-06-21
If you can provide a direct link to download the source I might be able to try and compile and eventually tell you exactly what to do. The problem is I can't understand [Japanese](http://www.v2p.jp/), and no translator at the moment.

---

### Post by Christmas on 2008-06-21
Nevermind, I got it from [here](http://www.v2p.jp/video/Viewer/Linux/). It looks like it's already a binary. Uncompress it, then install libglitz1:
```
sudo apt-get install libglitz1
```
Then just run it from inside that directory or using:
```
./lkeyholetv
```

---

### Post by The Pinny Parlour on 2008-06-21
> **Christmas said:**
> Nevermind, I got it from [here](http://www.v2p.jp/video/Viewer/Linux/). It looks like it's already a binary. Uncompress it, then install libglitz1:
```
sudo apt-get install libglitz1
```
Then just run it from inside that directory or using:
```
./lkeyholetv
```

Thanks for you help.  I can't get it to work.  It says 'bash: ./lkeyholetv: No such file or directory'

I downloaded and extracted it to the desktop.

---

### Post by Martje_001 on 2008-06-21
You have to 'cd' to the directory in a terminal:
```
cd /home/user/Desktop/extract-folder
```
and then launch it.

---

### Post by The Pinny Parlour on 2008-06-21
> **Martje_001 said:**
> You have to 'cd' to the directory in a terminal:
```
cd /home/user/Desktop/extract-folder
```
and then launch it.

Thank you.  One step further was made then this:
KeyHoleTV Can not Open DSP (/dev/dsp) 

It's a bit challenging.

---

### Post by The Pinny Parlour on 2008-06-21
This might help.  I don't really following it, and the things I tried completely failed.

OISEYER Inc.
                                                2008 5 / 31
                                               Takashi Kosaka

1 Introduction

Thank you very much to download KeyHoleTV 1.1. As Linux KeyHoleTV uses the following
dynamic link libraries: 

%ldd lkeyholetv 
        linux-gate.so.1 
        libgtk-x11-2.0.so.0
        libgdk-x11-2.0.so.0
        libatk-1.0.so.0 
        libgdk_pixbuf-2.0.so.0 
        libpangocairo-1.0.so.0 
        libpango-1.0.so.0 
        libcairo.so.2 => 
        libgobject-2.0.so.0
        libgmodule-2.0.so.0 
        libdl.so.2 
        libglib-2.0.so.0 
        libfreetype.so.6 
        libfontconfig.so.1 
        libXrender.so.1 
        libX11.so.6 
        libXext.so.6 
        libpng12.so.0 
        libz.so.1 
        libglitz.so.1 
        libm.so.6 
        libpthread.so.0 
        libc.so.6 
        libXrandr.so.2 
        libXi.so.6 
        libXinerama.so.1 
        libXcursor.so.1
        libXfixes.so.3 
        libpangoft2-1.0.so.0 
        /lib/ld-linux.so.2 
        libexpat.so.0 

If your environment dose not have some dynamic link libraries, please install libraries 
in the correct version. The current version of KeyHoleTV has tested on SuSE11.0 and 32bit gcc.  However KeyHoleTV dose not have tested other environments yet.

2 How to Install KeyHoleTV.

There is a “makefile” in the decompressed directory. Use a super user mode to type 
in shell the followings:

% make install

You may change the content of the “makefile” to the installed directory. However you have 
to use the following directories :

/usr/local/etc
/local/etc
/local/bin

KeyHoleTV searches the above directories to get pixmap and the server location data.
After installation, you may change an emblem for KeyHoleTV. There is a default pixmap 
for emblem in the decompressed directory  To execute KeyHoleTV, you can type "lkeyholetv",
if you have search paths. You can put a link of KeyHoleTV in yor desktop.

If you don't want to install KeyHoleTV, please go to the decompressed directory to type 
"lkeyholetv". In this case, you can not use a link because KeyHoleTV can not find the 
server host address.

3 How To UnInstall KeyHoleTV
 
Please go to the decompressed directory and become super user

% make uninstall

The makefile delete all KeyHoleTV related information in the installed directory.

4 Known Problem.

The current version of KeyHoleTV dose not start multiply  in your Linux environment. 
Also, some applications uses /dev/dsp, KeyHoleTV might not start.
The reason of the problem, KeyHoleTV opens /dev/dsp to make sound in 8000Hz, 16bit samples.
The current GNOME environment has a EsoundD (esd).  However EsoundD uses 44100 Hz and
16 bits sample. 

/* get the stream latency to esound (latency is number of samples  */
/* at 44.1khz stereo 16 bit - you'll have to adjust if oyur input  */
/* sampling rate is less (in bytes per second)                     */
/* so if you're at 44.1khz stereo 16bit in your stream - your lag  */
/* in bytes woudl be lag * 2 * 2 bytes (2 for stereo, 2 for 16bit) */
/* if your stream is at 22.05 Khz it'll be double this - in mono   */
/* double again ... etc.                                           */
  --- esd.h ---

If Linux environment has new version of EsoundD which supports multiple frequency and 
sampling, KeyHoleTV will support the target environment.

5 Please send me Bug report.

If you find bugs and comments, please use KeyHoleTV home page [www.v2p.jp/video/](www.v2p.jp/video/). 
You can use “inquiry”.

---

### Post by Christmas on 2008-06-21
Try this:
```
sudo modprobe snd-pcm-oss
```
It should work, it does for me. Eventually, also try:
```
sudo modconf
```
Then go down to *kernel/sound/core/oss* and make sure *snd-pcm-oss* has a plus (+). Then disable it and enable it again. Just be careful that the interface is a little tricky, you'll have to go back up and enter *Finish. Return to previous menu* in order to save the configuration (just use the arrow keys and Enter).

I had the same error but this fixed it, so it works for me. Nice little application:

LE: The problem I noticed is that it eats 100% CPU resources. This particular version looks to be badly done.

---

### Post by The Pinny Parlour on 2008-06-25
> **Christmas said:**
> Try this:
```
sudo modprobe snd-pcm-oss
```
It should work, it does for me. Eventually, also try:
```
sudo modconf
```
Then go down to *kernel/sound/core/oss* and make sure *snd-pcm-oss* has a plus (+). Then disable it and enable it again. Just be careful that the interface is a little tricky, you'll have to go back up and enter *Finish. Return to previous menu* in order to save the configuration (just use the arrow keys and Enter).

I had the same error but this fixed it, so it works for me. Nice little application:

LE: The problem I noticed is that it eats 100% CPU resources. This particular version looks to be badly done.

Great tips, thank you.   

I downloaded the new version (1.7) for Linux and it works much better then 1.4.  My cpu load is around the 15-25% mark.

Thanks again.

---

### Post by gigabz666 on 2008-07-02
I've installed the same program, and managed to get it working and playing great. One problem. I have no sound at all. I tried to follow the instructions for the sound to see if it would solve my problem and after installing modconf I was unable to find kernel/sound/core/oss.

I'm running Kubuntu Hardy. Any ideas?

---

### Post by Trying to switch on 2008-07-05
> **Christmas said:**
> Nevermind, I got it from [here](http://www.v2p.jp/video/Viewer/Linux/). It looks like it's already a binary. Uncompress it, then install libglitz1:
```
sudo apt-get install libglitz1
```
Then just run it from inside that directory or using:
```
./lkeyholetv
```
Thank you for your help. I use a lot of Japanese-related software and since I'm thinking about finally getting rid of Windows Vista I've been trying to replace that software with it's linux version or use Wine. So far so good, except for this program...

I first used make install and then I tried to do what you said in the post I quote, but when I use 
```
./lkeyholetv
```
I get
```
./lkeyholetv: error while loading shared libraries: libglitz.so.1: 
cannot open shared object file: No such file or directory

```
I already installed libglitz earlier using Synaptic though. When I enter```
sudo apt-get install libglitz1
```and my password I simply get```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglitz1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
```
I'm trying to run KeyHoleTV Version 1.11 from [http://www.v2p.jp/video/Viewer/Linux/](http://www.v2p.jp/video/Viewer/Linux/) on Ubuntu 8.04 Hardy Heron (64 bit I think) in Gnome with all the latest updates except those for evolution, openoffice and gnome games. The KeyHoleTV map is directly in my home directory and that's where I'm trying to run it from.

---

### Post by Bredymer on 2008-07-06
Trying to switch> I had similar problem as you, but then i realized that it's libglitz1 with the last letter being the number 1 and not a lower case L (both download and install something....)

Could be a possibility....

---

### Post by Trying to switch on 2008-07-07
Thanks, but I did use the number one instead of the letter l. To be certain I tried both once more and neither worked.

---

