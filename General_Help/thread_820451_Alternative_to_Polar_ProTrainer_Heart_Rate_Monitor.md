---
title: "Alternative to Polar ProTrainer Heart Rate Monitor software"
date: 2008-06-06
forum: General Help
---

### Post by hantabaru on 2008-06-06
Hi

I use Polar heart rates monitors in my job and I am looking for some software that allows me to view the files of heart rate data downloaded from the watches. I really don't want to to have to dual boot if I can help it and the virtualbox route feels a little advanced for me at this point. I have managed to get the Polar Protrainer software running with wine but it doesn't show the writing in the calender and I can't download the data from the watch.

Would really appreciate any help on this as it is a bit of a specialist area and hence there doesn't appear to be much info around,

Thanks in Advance

---

### Post by FrankVdb on 2008-06-14
I do Ironman triathlons and I've been using an Polar S625x heart-rate monitor for many many years.

I thought there was simply nothing for downloading the workouts to a Linux PC but Google learns me there are a number of applications we should try:

[http://opendevice.blogspot.com/2007/03/polar-heart-rate-monitors-on-linux.html](http://opendevice.blogspot.com/2007/03/polar-heart-rate-monitors-on-linux.html)

Haven't had the time to check it out though.

---

### Post by lordharaldi on 2008-09-19
Hi!

I bought the heart rate monitor Polar RS200. I couldn't find a easy to use application for Linux.
So I programmed a website which can handle the RS200.
Just record the SonicLink sound as .wav file and upload it to the website.
The website converts the sound file and displays statistics and charts.
I plan to support also the Garmin Forerunner 305 at the beginning of next year.
Also an export function will be included because everyone should be able to get the data out of the website. (within the next two month)
I will increase the functionality step by step.

My website: [http://lordharaldi.dyndns.org/wyw](http://lordharaldi.dyndns.org/wyw)

Greetings,
Harry

---

### Post by _sAm_ on 2008-09-19
Check this article H:
[http://www.linux.com/articles/60528](http://www.linux.com/articles/60528)

Harry; impressed, will try:-)

---

### Post by nardo_ARG on 2009-02-08
This a good solution.
[http://rs200-decoder.sourceforge.net/](http://rs200-decoder.sourceforge.net/)
I've compiled and tested on ubuntu 8.04 and works fine.
You porbably need to install build essential for compile.

Cheers

---

### Post by MilkSjeik on 2009-04-28
Does someone has an idea what hardware is supported as an USB IrDA adapater? Since I think the Polar IrDA device is quite expensive (and will it work on linux?). My guess is that other manufactures will also work? Anybody experience?

---

### Post by matthiayer on 2009-06-03
any updates on polar protrainer 5 with wine?

---

### Post by Yeti can't ski on 2010-01-07
> **nardo_ARG said:**
> This a good solution.
[http://rs200-decoder.sourceforge.net/](http://rs200-decoder.sourceforge.net/)
I've compiled and tested on ubuntu 8.04 and works fine.
You porbably need to install build essential for compile.

Cheers

Just an update, they now have binaries (version 0.9.0) that worked out of the box for me on 32-bits Karmic Koala. 

For newbies like myself, a step-by-step roadmap: 

I - Download the binaries: 

[http://sourceforge.net/projects/rs200-decoder/files/rs200-decoder/rs200_decode_0.9.0/rs200_decode_0.9.0_linux_binaries.tar.gz/download]("http://sourceforge.net/projects/rs200-decoder/files/rs200-decoder/rs200_decode_0.9.0/rs200_decode_0.9.0_linux_binaries.tar.gz/download")

II - Unpack the files in a specific directory; 

III - Open the terminal and go to such specific directory using "cd [name of directory]" command; 

IV - For help, type ```
./rs200_decode -h
```

V - For running the program with standard microphone: ```
./rs200_decode -m
```

V.A - Approach the RS200 to the microphone and start data transfer; and
V.B - Enjoy your training report! :-)

---

### Post by Remi78 on 2010-03-19
The Polar RS200 decoder is a very nice program. What makes it difficult to use is the fact that it relies on the OSS sound system. Present days (2010) Ubuntu distributions ship with ALSA sound system.

The ALSA website informs you about the possibility to emulate OSS by the ALSA soundsystem. [ [http://alsa.opensrc.org/index.php/OssEmulation](http://alsa.opensrc.org/index.php/OssEmulation) ].

I resolved the issue by installing the alsa-oss package and appending to /etc/modules the following modules:
snd-pcm-oss
snd-mixer-oss
snd-seq-oss

Happy running!

---

### Post by GrumpyBob on 2010-07-10
I have found the only way forward with my Polar CS600X is to run WinXP in VirtualBox. You need the VirtualBox package from Oracle rather than the Ubuntu repo version.  I use the Polar Pro Trainer software to download the files, which I then import into [GoldenCheetah]("http://goldencheetah.org") (available for Linux, Windows and MacOS), which is may favoured package for analysinf training data.  To import GPS data, I merge hrm and gpx files into tcx format using [Rainer Clasen's perl scripts]("http://www.zuto.de/project/workout/").

---

### Post by gamx on 2010-10-13
I had rs200_decode working with Lucid using -m /dev/dsp an it was working fine. In Maverick that does not work (it does not help that /dev/dsp does not exist now). I have tried prepending padsp but now it gives me this error. Any idea? Thanks

--- Polar RS-200 SonicLink decoder ---

Parameters passed:
Input file: (null)
Input from microphone
Input device: /dev/dsp
Output into directory
Output file: (null)
Output directory: /home/gamx/
Output format summary: 1
Output format csv: 0
Output format raw: 1
Output format xml: 1
Output format binary: 0
Unlimited read: 0

Debug: Reading data from microphone.

Debug: Decoding signal into bytes.

Debug: Errors in signal, restart reading.

..
Debug: Opening /dev/dsp for input
utils/padsp.c: dsp_open()
utils/padsp.c: fd_info_new()
utils/padsp.c: dsp_open() succeeded, fd=3
utils/padsp.c: SOUND_MIXER_WRITE_RECSRC

Debug: Recording source set to 0080

utils/padsp.c: unknown ioctl 0xc0044d07
ioctl(fd,SOUND_MIXER_WRITE_MIC,&val): Invalid argument

---

### Post by ebedebe on 2012-10-30
rs200_decode version supports PulseAudio is here: 
[http://urmet.cjb.net/blog/?page_id=66](http://urmet.cjb.net/blog/?page_id=66)
For compiling the source, you’ll need to install the libpulse-dev package.

---

### Post by howefield on 2012-10-30
Old thread back to sleep.

---

