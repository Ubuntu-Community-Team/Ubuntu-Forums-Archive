---
title: "VLC problems"
date: 2018-05-24
forum: General Help
---

### Post by John Jason Jordan on 2018-05-24
I recently did a dist-upgrade from Xubuntu 14.04 to 16.04.2, which went well except for the usual fixes that were needed. I've got everything repaired except for VLC, which I use a lot.

Prior to the dist-upgrade I had VLC 2.2.5 from a PPA, that had worked beautifully for me for a long time. The dist-upgrade disabled the PPA and installed 2.2.2. Unfortunately, I could not get screenshots working in 2.2.2, in spite of hours searching for a solution. I did find that someone had posted about this on the videolan forums and one of the moderators replied that it was a bug and was not going to be fixed since 3.0 had been released. And, while the PPA allowed me to install 2.2.5 a long time ago on 14.04, the PPA no longer works, so it looks like my current choices are 2.2.2 from the 16.04 repos, or 3.0.1.

So fine, I installed 3.0.1 with snap. Happily screenshots are working, but 3.0.1 has other even more annoying problems:
1) I cannot change the appearance of the toolbars. I get just one toolbar instead of the usual two, and I cannot add or delete buttons to it.
2) VLC always opens in a small window in the middle of the screen. I drag it to the size I want it to be, close it, and when I reopen it, it is still a small window in the middle of the screen. All other programs on this computer remember their window size, including other video players, but not VLC. And this happens whether I open it from the file manager with a video file, or just launch it empty from the application menu. And yes, I unchecked   the box in Preferences so it is not supposed to resize its window to match the video.

I have spent hours on these problems and I'm out of ideas. I could really use some suggestions.

---

### Post by ajgreeny on 2018-05-24
I am using VLC 2.2.2 Weatherwax version according to its own Help menu on Xubuntu 16.04, and that will take a screenshot using Shift+S keyboard shortcut, or using "Take snapshot" at the bottom of the Video menu items.

---

### Post by John Jason Jordan on 2018-05-24
> **ajgreeny said:**
> I am using VLC 2.2.2 Weatherwax version according to its own Help menu on Xubuntu 16.04, and that will take a screenshot using Shift+S keyboard shortcut, or using "Take snapshot" at the bottom of the Video menu items.

Thanks for saying that; at least I know it is supposed to be working on Xubuntu.

I have made progress:

I uninstalled 3.0.1 (sudo snap remove vlc). I think I'd also like to uninstall snap as well, but later for that.

Then I renamed all the .vlc config files I could find. And then I installed VLC from the 16.04 repositories (sudo apt-get install vlc). I could swear that the dist-upgrade installed 2.2.2, but this time I got 2.2.7 'Umbrella.' I launched it without a file and noted that it still had only one toolbar on the bottom, and that toolbar was lacking the icon for 'take screenshot.' Nevertheless, I resized its window to the way I wanted it, then shut it down and re-launched it. This time the window came up exactly as I had resized it. (Yay!) Then I closed it and re-opened it by opening a .mkv file from the file manager. Again, it came up as before, except it resized its window to the video resolution, so I unchecked the box for that in Preferences, shut it down, and restarted it with the same video. This time it came up as I wanted it to.

Finally I attacked the toolbar problem. As with previous attempts I was unable to get it the way I wanted it, except that after half an hour of swearing at it I finally got the group of buttons that contains the 'take screenshot' button visible. To do this I moved everything from Line 2 into Line 1, and then dragged the 'take screenshot' group from Line 1 into Line 2. I now have a Line 1 with Play etc. and a Line 2 with just the 'take screenshot' group. Looks kind of silly, but at least now I can access the features that I need.

The Tools > Customize Interface dialog box needs a lot of work. Most of the drag and drop things appear to work in the dialog box, but don't affect what appears in the main window. The dialog box desperately needs an 'Apply' button that would make the main window reflect the changes you just made. Some instructions would also help. Ah, well, another saga in my endless love/hate affair with VLC come to a close.

---

### Post by monkeybrain20122 on 2018-05-24
Not sure what your problem is. maybe because the snap package is broken (snap is an experimental technology). Here I have vlc-3.0.3 on Ubuntu 16.04.4. No problem taking snapshot and the toolbars look complete to me. I compiled from source (which is really quite easy): install the build tools

```
sudo apt install automake build-essential checkinstall
```

then the dependencies
```
sudo apt build-dep vlc
```

Then download the [tarball]("http://get.videolan.org/vlc/3.0.2/vlc-3.0.2.tar.xz") from videolan, right click and extract, cd into its directory

```
./bootstrap

./configure
```

Now look at the output of configure, see if anything you need is missing, if all looks ok and without errors.

```
make -j4 

``` (-j4 means use 4 threads, if you have more or less just adjust that)

then 

```
sudo checkinstall
``` and follow the prompts, it will install a nice .deb

If you don't feel like doing the work, you can get vlc-4.0.0 beta from vlc's [ppa]("https://launchpad.net/~videolan/+archive/ubuntu/master-daily") (this is master, the one you used to had stopped working for a long time) I have vlc-4 beta on my 18.04 machine, it works very well, but I compiled it myself rather than installing from the ppa

**Edited: **ffmpeg from Ubuntu 16.04 may be too old for compiling vlc-3.0.x ( I don't know since I have upgraded mine long ago) if there is a problem upgrade ffmpeg from [here]("https://launchpad.net/~mc3man/+archive/ubuntu/xerus-media")
```
sudo add-apt-repository ppa:mc3man/xerus-media
sudo apt update
sudo apt install ffmpeg

```

**More Edited: **Turns out the mc3man ppa also has  vlc-2.2.8. If you don't mind it being too old (you probably don't since it is newer than  your version) you can simply add that ppa and install vlc and **skip all the above**.

---

### Post by John Jason Jordan on 2018-05-24
@monkeybrain:

I thought I had it fixed, but suddenly screenshots are not working. I started on your suggestions uninstalling VLC and then adding the master-daily ppa, which went OK, but no new versions of VLC showed up in Synaptic. So then I tried your code, but the second command failed with:

```
jjj@Devil-Bonobo:/media/jjj/Movies$ sudo apt build-dep vlc
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 builddeps:vlc : Depends: libx264-dev (>= 2:0.86) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

So then I reinstalled VLC (this time I got 2.2.2), and screenshots were still not working. So I shut it down and relaunched from the command line, and this time I got some big clues:

```
jjj@Devil-Bonobo:/media/jjj/Movies$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80)
[0000000001157148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
QXcbWindow: Unhandled client message: "_GTK_LOAD_ICONTHEMES"
QXcbWindow: Unhandled client message: "_GTK_LOAD_ICONTHEMES"
QXcbWindow: Unhandled client message: "_GTK_LOAD_ICONTHEMES"
QXcbWindow: Unhandled client message: "_GTK_LOAD_ICONTHEMES"
[ass] Shaper: FriBidi 0.19.7 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Using font provider fontconfig
[00007f75a8ce41f8] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  384.111  Tue Dec 19 22:55:29 PST 2017 for hardware decoding.
[00007f75c816dab8] core filter error: Failed to create video filter2
[00007f75c809b528] vdpau_chroma filter error: corrupt VDPAU video surface 0x7f7580114bf0
[00007f75ac1ac038] core video output error: Failed to convert image for snapshot
[00007f75c81bcfb8] core filter error: Failed to create video filter2
[00007f75c80ebbd8] vdpau_chroma filter error: corrupt VDPAU video surface 0x7f758008bf60
[00007f75ac1ac038] core video output error: Failed to convert image for snapshot
QObject::~QObject: Timers cannot be stopped from another thread
```

I searched on 'vdpau' in Synaptic and the installed modules are vdpau-va-driver 0.7.4-5, mesa-vdpau-drivers 17.2.8, and vdpau-driver-all 1.1.3. For VLC the installed modules are (all 2.2.2-5) vlc vlc-plugin-samba, vlc-data, vlc-plugin-notify, libvlccore8, and vlc-nox. 

I hope some of that spurs additional suggestions and clues. :)

---

### Post by monkeybrain20122 on 2018-05-24
Ok, I think maybe just try mc3man's vlc-2.2.8. 

close all vlc instances, delete the folder ~/.config/vlc (.config is a hidden folder with a "." in front)

Uninstall all your vlc packages, disable the vlc master ppa (Software & Updates > Other Software > uncheck the box for that ppa)
Now add mc3man's ppa

update then install vlc.

---

### Post by John Jason Jordan on 2018-05-24
OK, I got 2.2.8 installed and a new ffmpeg. But I still can't get screenshots to work. Launching it from the command line I get the following:

```
jjj@Devil-Bonobo:/media/jjj/Movies$ vlc
VLC media player 2.2.2 Weatherwax (revision 2.2.2-0-g6259d80) *(sic, the Help > About says 2.2.8)*
[0000000000a54148] core libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[ass] Shaper: FriBidi 0.19.7 (SIMPLE) HarfBuzz-ng 1.0.1 (COMPLEX)
[ass] Using font provider fontconfig
[00007fc5f4ce32e8] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  384.111  Tue Dec 19 22:55:29 PST 2017 for hardware decoding.
[00007fc6180d6a58] core filter error: Failed to create video filter2
[00007fc6180d0f28] vdpau_chroma filter error: corrupt VDPAU video surface 0x7fc5d0089ad0
[00007fc5fc1ac018] core video output error: Failed to convert image for snapshot
[00007fc6181c3f88] core filter error: Failed to create video filter2
[00007fc6181bc098] vdpau_chroma filter error: corrupt VDPAU video surface 0x7fc5d0089ad0
[00007fc5fc1ac018] core video output error: Failed to convert image for snapshot
^CQObject::~QObject: Timers cannot be stopped from another thread
```

I don't know what is going on with VDPAU. It appears that VDPAU is the reason that screenshots are not working. I mentioned above which modules are listed in Synaptic as installed. All I know about VDPAU is that it is part of the nVIDIA driver that I am using. The driver GUI says it supports MPEG1, MPEG2, H264, VC1, MPEG4, DIVX4, and DIVX5.

---

### Post by monkeybrain20122 on 2018-05-24
I think you have some issues with the Nvidia driver.. How did you install it? I mean from the repo, from the run file or upgrade from 14.04? 

Also install these packages
```

sudo apt install mesa-utils vdpauinfo
```


then post the outputs of

```
vdpauinfo
```

and
```

glxinfo | grep OpenGL
```

---

### Post by John Jason Jordan on 2018-05-25
First I installed mesa-utils and vdpauinfo and then tried VLC again. Still no screenshots.

Here is vdpauinfo:
```
jjj@Devil-Bonobo:/media/jjj/Movies$ vdpauinfo
display: :0   screen: 0
API version: 1
Information string: NVIDIA VDPAU Driver Shared Library  384.111  Tue Dec 19 22:55:29 PST 2017

Video surface:

name   width height types
-------------------------------------------
420     4096  4096  NV12 YV12 
422     4096  4096  UYVY YUYV 

Decoder capabilities:

name                        level macbs width height
----------------------------------------------------
MPEG1                           0 65536  4032  4048
MPEG2_SIMPLE                    3 65536  4032  4048
MPEG2_MAIN                      3 65536  4032  4048
H264_BASELINE                  41 65536  4032  4080
H264_MAIN                      41 65536  4032  4080
H264_HIGH                      41 65536  4032  4080
VC1_SIMPLE                      1  8190  2048  2048
VC1_MAIN                        2  8190  2048  2048
VC1_ADVANCED                    4  8190  2048  2048
MPEG4_PART2_SP                  3  8192  2048  2048
MPEG4_PART2_ASP                 5  8192  2048  2048
DIVX4_QMOBILE                   0  8192  2048  2048
DIVX4_MOBILE                    0  8192  2048  2048
DIVX4_HOME_THEATER              0  8192  2048  2048
DIVX4_HD_1080P                  0  8192  2048  2048
DIVX5_QMOBILE                   0  8192  2048  2048
DIVX5_MOBILE                    0  8192  2048  2048
DIVX5_HOME_THEATER              0  8192  2048  2048
DIVX5_HD_1080P                  0  8192  2048  2048
H264_CONSTRAINED_BASELINE      41 65536  4032  4080
H264_EXTENDED                  41 65536  4032  4080
H264_PROGRESSIVE_HIGH          41 65536  4032  4080
H264_CONSTRAINED_HIGH          41 65536  4032  4080
H264_HIGH_444_PREDICTIVE       41 65536  4032  4080
HEVC_MAIN                      --- not supported ---
HEVC_MAIN_10                   --- not supported ---
HEVC_MAIN_STILL                --- not supported ---
HEVC_MAIN_12                   --- not supported ---
HEVC_MAIN_444                  --- not supported ---

Output surface:

name              width height nat types
----------------------------------------------------
B8G8R8A8         16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 
R10G10B10A2      16384 16384    y  Y8U8V8A8 V8U8Y8A8 A4I4 I4A4 A8I8 I8A8 

Bitmap surface:

name              width height
------------------------------
B8G8R8A8         16384 16384
R8G8B8A8         16384 16384
R10G10B10A2      16384 16384
B10G10R10A2      16384 16384
A8               16384 16384

Video mixer:

feature name                    sup
------------------------------------
DEINTERLACE_TEMPORAL             y
DEINTERLACE_TEMPORAL_SPATIAL     y
INVERSE_TELECINE                 y
NOISE_REDUCTION                  y
SHARPNESS                        y
LUMA_KEY                         y
HIGH QUALITY SCALING - L1        y
HIGH QUALITY SCALING - L2        -
HIGH QUALITY SCALING - L3        -
HIGH QUALITY SCALING - L4        -
HIGH QUALITY SCALING - L5        -
HIGH QUALITY SCALING - L6        -
HIGH QUALITY SCALING - L7        -
HIGH QUALITY SCALING - L8        -
HIGH QUALITY SCALING - L9        -

parameter name                  sup      min      max
-----------------------------------------------------
VIDEO_SURFACE_WIDTH              y         1     4096
VIDEO_SURFACE_HEIGHT             y         1     4096
CHROMA_TYPE                      y  
LAYERS                           y         0        4

attribute name                  sup      min      max
-----------------------------------------------------
BACKGROUND_COLOR                 y  
CSC_MATRIX                       y  
NOISE_REDUCTION_LEVEL            y      0.00     1.00
SHARPNESS_LEVEL                  y     -1.00     1.00
LUMA_KEY_MIN_LUMA                y  
LUMA_KEY_MAX_LUMA                y  
```

And here is glxinfo:
```
jjj@Devil-Bonobo:/media/jjj/Movies$ glxinfo | grep OpenGL
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce GTX 765M/PCIe/SSE2
OpenGL core profile version string: 4.5.0 NVIDIA 384.111
OpenGL core profile shading language version string: 4.50 NVIDIA
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.5.0 NVIDIA 384.111
OpenGL shading language version string: 4.50 NVIDIA
OpenGL context flags: (none)
OpenGL profile mask: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.2 NVIDIA 384.111
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20
OpenGL ES profile extensions:
```

I don't recall for sure whether the nVIDIA driver was installed from the repos or from nVIDIA's website. If it was from the repos it would have been 14.04, but I suspect it was from nVIDIA. I recall at the time that I had originally installed the nouveau driver on the initial installation, but it was giving me problems so I switched to the proprietary driver. And whatever version I have now is whatever I started with, plus possibly changes made by the dist-upgrade. Hmmm. I think I'll go see what version is on nVIDIA's website.

---

### Post by monkeybrain20122 on 2018-05-25
The outputs look ok to me.

BUT If your driver is an "upgrade" from 14.04 then you should reinstall it. Normally you should purge the driver before you upgrade, it normally won't survive the upgrade and if it does by some miracle it would be broken likely.

**Don't use the .run file from Nvidia**, get it from the repo.  You should get the nvidia-340-updates for the GTX 765M [http://www.nvidia.com/Download/driverResults.aspx/130042/en-us](http://www.nvidia.com/Download/driverResults.aspx/130042/en-us) 


P.S. to make life easier you should get synaptic the gui-package manager then you can see at a glance what is available without mugging around with command line and getting wrong package names etc.

---

### Post by John Jason Jordan on 2018-05-25
Well, I looked at the NVIDIA website and 384.111 is in the drivers available for download, but the version that is installed (and just now reinstalled) is 384.111-0ubuntu0.16.04.1, which looks like I installed it from the Ubuntu repos. And the date was 12/19/2017, barely five months ago. And now I remember that I went to the NVIDIA website to figure out which driver to install for my GTX 765M, but I installed it from the repos.

And yes, Synaptic is the first thing I add after a new install. I use both Synaptic and the command line because usually one will be easier than the other. And I used it just now to reinstall 384.111. Sadly, the re-installation did not fix the snapshot problem.

OMIGOD, I just found the solution! I googled on "[00007f3e80124368] vdpau_chroma filter error: corrupt VDPAU video surface 0x7f3e38089ad0" and it popped up an Ubuntu page: [https://askubuntu.com/questions/769585/vlc-cant-take-snapshots-anymore-due-to-corrupt-vdpau-video-surface-error#770040]("https://askubuntu.com/questions/769585/vlc-cant-take-snapshots-anymore-due-to-corrupt-vdpau-video-surface-error#770040"). I followed the instructions and changed Hardware-accelerated Decoding from 'Automatic' to 'VA-API video decoder via X11.' Voilà! Snapshots are now working!

Thanks a million for the help! I couldn't have figured this all out myself.

---

### Post by ajgreeny on 2018-05-26
Brilliant news!  The **automatic** option in the Input & Codecs section of VLC's preferences can occasionally have a much greater effect than anyone would believe.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

