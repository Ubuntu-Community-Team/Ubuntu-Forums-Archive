---
title: "DVD Issues in 16.04"
date: 2016-02-01
forum: General Help
---

### Post by matt082606 on 2016-02-01
Forgive me if this is not the proper place for this.

I have recently installed 16.04 for testing and updating drivers. It seems like everything works, even got Netflix working out of the box. 

The issue I am having is finding the codecs for DVD player. Which is strange, I've never had this issue before. I have tried the usual suspects and no luck. Best I can get is VLC player to recognize, display the title and then revert back to nothing loaded with no error or notification. This is on multiple DVDs tried. Parole gives me the standard, backend error - missing codec -et cetera, but I have installed all the proper improper codecs that should be required. Any one have an idea or would like to help me tackle this?

lsdvd gives me a proper understanding of the disk, title, chapters, lengths, so forth. Yet I cannot seem to get this working.

lsscsi gives me this:
[2:0:0:0]    cd/dvd  MATSHITA DVD-RAM UJ8C0    1.00  /dev/sr0

This is not an area I really want to spend a lot of time. I have been taking for granted how easy this has been in the past.

Thanks for looking.

---

### Post by howefield on 2016-02-01
Thread moved to the "*Ubuntu Development Version*" forum.

---

### Post by QDR06VV9 on 2016-02-01
From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.


Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line:

```
sudo apt-get install libdvd-pkg
```


Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
Source: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by kansasnoob on 2016-02-01
> **runrickus said:**
> From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.


Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line:

```
sudo apt-get install libdvd-pkg
```


Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
Source: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Thanks for that info, I wasn't aware of the change.

---

### Post by QDR06VV9 on 2016-02-01
:D I have to refer to the wiki's a lot, I just can not keep up with the newer methods and changes..
Kind Regards

---

### Post by matt082606 on 2016-02-03
> **runrickus said:**
> From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.


Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line:

```
sudo apt-get install libdvd-pkg
```


Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
Source: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Many, many thanks.

---

### Post by matt082606 on 2016-02-04
> **runrickus said:**
> From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.


Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line:

```
sudo apt-get install libdvd-pkg
```


Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
Source: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Okay,
I installed this yesterday, and today I tried to play a DVD again. Still no luck. I ran VLC from terminal to capture what it is going through. 

Here is the complete output after typing vlc:
```

VLC media player 2.2.1 Terry Pratchett (Weatherwax) (revision 2.2.1-0-ga425c42)
[00000000022ca158] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: PHISH_BITTERSWEET_MOTEL
libdvdnav: DVD Serial Number: 3A8206DC___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000151
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00063c97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00066c88
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00066cd6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002b7e1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002b7e69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002bd218
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002bd266
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002ed2b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ed2fe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002f5623
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002f5671
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0030e21c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0030e26a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0031a07b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0031a0c9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0036d73c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0036d78a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003756ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0037573a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0037bd42
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0037bd90
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0
[00007f82c80009b8] core input error: ES_OUT_RESET_PCR called
[00007f82c80009b8] core input error: ES_OUT_RESET_PCR called
[00007f82c80009b8] core input error: ES_OUT_RESET_PCR called
[00007f82c80009b8] core input error: ES_OUT_RESET_PCR called

```

Here is the output when using Parole:
```

libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: PHISH_BITTERSWEET_MOTEL
libdvdnav: DVD Serial Number: 3A8206DC___MVB__
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00000151
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000001d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00063c97
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00066c88
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x00066cd6
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x002b7e1b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x002b7e69
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x002bd218
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x002bd266
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x002ed2b0
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x002ed2fe
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x002f5623
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x002f5671
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_0.VOB at 0x0030e21c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_07_1.VOB at 0x0030e26a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_0.VOB at 0x0031a07b
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_08_1.VOB at 0x0031a0c9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_0.VOB at 0x0036d73c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_09_1.VOB at 0x0036d78a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_0.VOB at 0x003756ec
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_10_1.VOB at 0x0037573a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_0.VOB at 0x0037bd42
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_11_1.VOB at 0x0037bd90
libdvdread: Elapsed time 0
libdvdread: Found 11 VTS's
libdvdread: Elapsed time 0

(parole:4738): parole-gst-WARNING **: Failed to query element position: chapter

```
It ends with a GStreamer backend error - Could not read DVD. This may be because the DVD is encrypted and a DVD decryption library is not installed.

This isn't really important for me on this machine, I am just frustrated that it doesn't.

Edit:
I'm wondering if I should uninstall libdvdread and libdvdnav and re-install libdvd-pkg. Maybe since I went the old route first I broke it?

---

### Post by QDR06VV9 on 2016-02-04
That might work! I already had it installed when I changed to xenial.
But give this a go..
```
[COLOR=#333333][FONT=UbuntuMono]sudo apt-get install libdvdread4[/FONT][/COLOR]
```
[COLOR=#333333][FONT=Ubuntu]Then open a terminal window and execute:
[/FONT][/COLOR]```
[COLOR=#333333][FONT=UbuntuMono]sudo /usr/share/doc/libdvdread4/install-css.sh[/FONT][/COLOR]
```[COLOR=#333333][FONT=Ubuntu]
And just to be sure install ubuntu-restricted.
```
[/FONT][/COLOR]sudo apt-get install ubuntu-restricted-extras[COLOR=#333333][FONT=Ubuntu]
```
[/FONT][/COLOR]Rebooting may be necessary.;)
It would be a big deal to me if they did not work I rely on media(DVD Avi and CD's) for some of my back-ups..
Let us know!

---

### Post by mc4man on 2016-02-04
At least here "sudo apt-get install libdvd-pkg" didn't actually install libdvdcss2, just libdvd-pkg, as in - 
"Setting up libdvd-pkg (1.4.0-1-1) ...
libdvd-pkg: dpkg database is locked. You may need to use command "sudo dpkg-reconfigure libdvd-pkg".

(- there was obviously nothing else locking  dpkg other than the above orig apt-get command.
Running the suggested command actually did get, build & install libdvdcss2

As far as vlc - "core input error: ES_OUT_RESET_PCR called" is irrelevant to your dvd playback issues, just typical vlc nonsense.

I'd, in order, for **16.04** - 
make sure libdvdcss2 is actually installed
**delete ~/.dvdcss folder**
With dvd already in your drive (assumes default device of /dev/sr0) start vlc as such & see if dvd plays. If not read thru log file in Home folder
```
export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2
```
followed by 
```
export LIBOVERLAY_SCROLLBAR=0 && vlc dvd:// > vlc_output.log 2>&1
```

---

### Post by cariboo on 2016-02-04
Did you run:

```
sudo dpkg-reconfigure libdvd-pkg
```

after installing libdvd-pkg?

---

### Post by QDR06VV9 on 2016-02-05
> **cariboo said:**
> Did you run:

```
sudo dpkg-reconfigure libdvd-pkg
```

after installing libdvd-pkg?
+1;)

---

### Post by matt082606 on 2016-03-11
Sorry for the late reply. I did try
```
sudo dpkg-reconfigure libdvd-pkg
```
It gave me a response like, "libdvd-pkg already installed" or something similar.

Ultimately I did a fresh install and went through all of the steps correctly and it did work. I am certain that my earlier attempts caused something to be in conflict or not configured properly and I did not want to take the time to trace it out. I am now running 16.04 with 4.4.0 kernel and everything works very well. 

Hopefully the info this thread brought up will be useful to someone searching and they can easily follow these two pieces of advice to correctly get DVD working before they break it.



> **runrickus said:**
> From Ubuntu 15.10 onwards, libdvd-pkg is available to ease the installation of libdvdcss.


Install the libdvd-pkg package (no need to add third party repositories) via Synaptic or command line:

```
sudo apt-get install libdvd-pkg
```


Follow libdvd-pkg's instructions to let it download, compile, and install libdvdcss.
Source: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)



> **cariboo said:**
> Did you run:

```
sudo dpkg-reconfigure libdvd-pkg
```

after installing libdvd-pkg?

---

### Post by GHPS on 2016-06-27
Switching from 14.04 to 16.04 I had the same problem. Even with
```
sudo apt-get install libdvd-pkg
sudo dpkg-reconfigure libdvd-pkg
```
the picture in VLC was corrupted and I got the "core input error: ES_OUT_RESET_PCR called" described above.
Yet playback in Dragon-Player was fine. So my first guess was to search in VLC for the cause of the problem.

After some testing I found the culprit: The automatic "input/codec" decoder selects VDPAU - 
which (at least in my case of Kubuntu 16.04-64) didn't work. Selecting - under "Settings/Input" - 
the VA-API hardware decoder (either DRM or X11) fixed the problem.

---

### Post by cariboo on 2016-06-27
Moved to General Help.

---

### Post by GHPS on 2016-07-21
Today I went a bit deeper into the rabbit hole:

1) Software

[LIST]
[*]The problem is not specific to DVD- but to MPEG1-playback.
All material encoded in "MPEG-1/2 (mpegv)" is effected.
(This piece of information will be relevant later.) 
[*]Therefore this problem is not effected by the physical DVD
drive parameters (e.g. region settings). 
[*]All current versions of VLC are effected - the version distributed
with 16.04 LTS (2.2.2 "Weatherwax") and also the latest build 
development version ppa (3.0.0-git20160527 "Vetinari"). 
[/LIST]
2) Hardware

[LIST]
[*]The problem is hardware specific: With an identical, cloned
disk image booted on different machines the blocky artifacts
of the picture were or were not present. All of my Thinkpad T60s
are affected (without regard to processor or memory), the Thinkpad
X201 was fine. Obviously the different graphics subsystem is
decisive here: The T60s have ATI chipsets and use the radeon
drivers, the X201 uses the onboard intel chipset and driver
(which is why I had to manually install libvdpau-va-gl1 here). 
[*]Installing and running vdpauinfo reveals the different capabilities
of the chipsets/drivers: The radeon driver claims 
[/LIST]
```
display: :0   screen: 0                                                                     

API version: 1                                                                                  
Information string: G3DVL VDPAU Driver Shared Library version 1.0                                     
                                                                                                      
Video surface:                                                                                               
                                                                                                             
name   width height types                                                                                              
-------------------------------------------                                                                            
420     4096  4096  NV12 YV12                                                                                                 
422     4096  4096                                                                                                            
444     4096  4096  Y8U8V8A8 V8U8Y8A8                                                                                                  
                                                                                                                                       
Decoder capabilities:                                                                                                                  
                                                                                                                                       
name                        level macbs width height                                                                                                  
----------------------------------------------------                                                                                                  
MPEG1                           0 65536  4096  4096                                                                                                   
MPEG2_SIMPLE                    3 65536  4096  4096                                                                                                   
MPEG2_MAIN                      3 65536  4096  4096                                                                                                   
H264_BASELINE                  --- not supported ---                                                                                                  
H264_MAIN                      --- not supported ---                                                                                                              
H264_HIGH                      --- not supported ---                                                                                                              
VC1_SIMPLE                     --- not supported ---                                                                                                              
VC1_MAIN                       --- not supported ---                                                                                                              
VC1_ADVANCED                   --- not supported ---                                                                                                              
MPEG4_PART2_SP                 --- not supported ---                                                                                                                         
MPEG4_PART2_ASP                --- not supported ---                                                                                                                         
DIVX4_QMOBILE                  --- not supported ---                                                                                                                         
DIVX4_MOBILE                   --- not supported ---
```[INDENT]and intel driver doesn't support MPEG1/2 decoding, only H_264. 
[/INDENT]

[LIST]
[*]VLC (vlc -v -v -v) finds the respective hardware decoders and takes them
into account before playing back an MPEG1/2 file. 
[/LIST]
 ```
[00007f5658c07888] avcodec decoder debug: available hardware decoder output format 16 (xvmcidct)
[00007f5658c07888] avcodec decoder debug: available hardware decoder output format 38 (vdpau_mpeg2)
[00007f5658c07888] avcodec decoder debug: available hardware decoder output format 109 (vdpau)
[00007f5658c07888] avcodec decoder debug: available hardware decoder output format 53 (vaapi_vld)
[00007f5658c07888] avcodec decoder debug: available software decoder output format 0 (yuv420p)
[00007f5650c0f738] core spu text debug: looking for text renderer module matching "any": 2 candidates
...
[00007f564c000b98] vdpau_display vout display debug: using back-end G3DVL VDPAU Driver Shared Library version 1.0
[00007f564c000b98] vdpau_display vout display debug: using RGBA format 2
[00007f564c000b98] vdpau_display vout display debug: using X11 window 0x01e00001
[00007f564c000b98] core vout display debug: using vout display module "vdpau_display"
[00007f564c000b98] core vout display debug: A filter to adapt decoder VDV0 to display VDOR is needed
[00007f564c1255d8] core filter debug: looking for video filter2 module matching "any": 64 candidates
[00007f564c1255d8] vdpau_chroma filter debug: using video mixer temporal deinterlace feature
[00007f564c1255d8] vdpau_chroma filter debug: using video mixer sharpness feature
[00007f564c1255d8] vdpau_chroma filter debug: using video mixer 7
[00007f564c1255d8] core filter debug: using video filter2 module "vdpau_chroma"
[00007f564c000b98] core vout display debug: Filter 'VDPAU' (0x7f564c1255d8) appended to chain
[00007f5650c0cee8] core video output debug: original format sz 1920x1080, of (0,0), vsz 1920x1080, 4cc VDV0, sar 1:1, msk r0x0 g0x0 b0x0
```[INDENT]Which is a good idea but fails...


[/INDENT]
 3) Back to Software
[LIST]
[*]The question now is whether VLC or VPDAU causes the problem.
Running mplayer (which has VPDAU hardware decoder support
as well) gives the answer: mplayer -vo vpdau -vc ffmpeg12vdpau file.vob
Here the output video is distorted the same way as in VLC.
The problem is located in VPDAU (or the mesa driver). 
[*]This becomes visible in VLC with version 2.2.2 where VDPAU 
is enabled by default. 
[/LIST]
  4) Conclusion

The verdict is quite clear: libvdpau seems to have a bug supporting
MPEG1/2 codecs on radeon hardware.  This can be seen in VLC but also
in mplayer playing back e.g. DVDs.

Solution: Turning away from VDPAU fixes the problem in all cases.
Simply disable hardware decoders or set to VA_API (which in my
case had the same result since no VA_API is installed).

---

