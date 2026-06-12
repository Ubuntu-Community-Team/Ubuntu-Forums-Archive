---
title: "need help to install subsonic"
date: 2017-05-12
forum: General Help
---

### Post by hilario_ferreira on 2017-05-12
HI all:

I'm trying to install subsonic following those instructions:
[http://www.subsonic.org/pages/installation.jsp#debian](http://www.subsonic.org/pages/installation.jsp#debian)

When I enter the [B]sudo dpkg -i subsonic-x.x.deb 

I get the message that file or directory not found !!!

what am I doing wrong ??
[/B]

---

### Post by steeldriver on 2017-05-12
Have you changed directory to the location where you downloaded the .deb file? are you replacing x.x with the correct release number for the version you downloaded?

---

### Post by hilario_ferreira on 2017-05-12
Well I downloaded the .deb file to my download folder, what do I have to do with this file ?? I have to move it to somewhere else ??(sorry but I'm new to linux world)

Of course when I entered the sudo dpkg .... i have changed the "x "  with the version number.

---

### Post by #&amp;thj^% on 2017-05-12
Just enter this in a terminal:
```
cd Downloads && sudo dpkg -i subsonic-6.0.deb
```

---

### Post by hilario_ferreira on 2017-05-12
> **1fallen said:**
> Just enter this in a terminal:
```
cd Downloads && sudo dpkg -i subsonic-6.0.deb
```

I get the same :file or directory not found

---

### Post by howefield on 2017-05-12
If the file is called subsonic-6.0.deb and is in the ~/Downloads folder (if not, then amend the command to suit).. the following should work.

```
sudo apt install ~/Downloads/subsonic-6.0.deb
```

For example...

```
sudo apt install ~/Downloads/subsonic-6.0.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'subsonic' instead of '/home/hugh/Downloads/subsonic-6.0.deb'
The following additional packages will be installed:
  ffmpeg libavdevice57 libavfilter6 libavresample3 libbs2b0 libebur128-1 libflite1 libopenal-data libopenal1 libopencv-core2.4v5
  libopencv-imgproc2.4v5 libpostproc54 librubberband2v5 libsdl2-2.0-0 libtbb2
Suggested packages:
  ffmpeg-doc
The following NEW packages will be installed
  ffmpeg libavdevice57 libavfilter6 libavresample3 libbs2b0 libebur128-1 libflite1 libopenal-data libopenal1 libopencv-core2.4v5
  libopencv-imgproc2.4v5 libpostproc54 librubberband2v5 libsdl2-2.0-0 libtbb2 subsonic
0 to upgrade, 16 to newly install, 0 to remove and 0 not to upgrade.
Need to get 17.4 MB/76.0 MB of archives.
After this operation, 40.3 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libavresample3 amd64 7:3.2.4-1build2 [52.5 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libbs2b0 amd64 3.1.0+dfsg-2.2 [10.5 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libebur128-1 amd64 1.2.0-2 [14.6 kB]
Get:4 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libflite1 amd64 2.0.0-release-3 [12.9 MB]
Get:5 /Data/Downloads/subsonic-6.0.deb subsonic all 6.0 [58.5 MB]
Get:6 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libtbb2 amd64 4.4~20160526-0ubuntu2 [111 kB]                                
Get:7 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libopencv-core2.4v5 amd64 2.4.9.1+dfsg1-2 [655 kB]                          
Get:8 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libopencv-imgproc2.4v5 amd64 2.4.9.1+dfsg1-2 [607 kB]                       
Get:9 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libpostproc54 amd64 7:3.2.4-1build2 [52.4 kB]                               
Get:10 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 librubberband2v5 amd64 1.8.1-6ubuntu2 [85.3 kB]                            
Get:11 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libavfilter6 amd64 7:3.2.4-1build2 [767 kB]                                
Get:12 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libopenal-data all 1:1.17.2-4 [101 kB]                                     
Get:13 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libopenal1 amd64 1:1.17.2-4 [207 kB]                                       
Get:14 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libsdl2-2.0-0 amd64 2.0.5+dfsg1-2ubuntu3 [361 kB]                          
Get:15 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 libavdevice57 amd64 7:3.2.4-1build2 [72.2 kB]                              
Get:16 http://gb.archive.ubuntu.com/ubuntu zesty/universe amd64 ffmpeg amd64 7:3.2.4-1build2 [1,492 kB]                                    
Fetched 17.4 MB in 48s (361 kB/s)                                                                                                          
Selecting previously unselected package libavresample3:amd64.
(Reading database ... 230783 files and directories currently installed.)
Preparing to unpack .../00-libavresample3_7%3a3.2.4-1build2_amd64.deb ...
Unpacking libavresample3:amd64 (7:3.2.4-1build2) ...
Selecting previously unselected package libbs2b0:amd64.
Preparing to unpack .../01-libbs2b0_3.1.0+dfsg-2.2_amd64.deb ...
Unpacking libbs2b0:amd64 (3.1.0+dfsg-2.2) ...
Selecting previously unselected package libebur128-1:amd64.
Preparing to unpack .../02-libebur128-1_1.2.0-2_amd64.deb ...
Unpacking libebur128-1:amd64 (1.2.0-2) ...
Selecting previously unselected package libflite1:amd64.
Preparing to unpack .../03-libflite1_2.0.0-release-3_amd64.deb ...
Unpacking libflite1:amd64 (2.0.0-release-3) ...
Selecting previously unselected package libtbb2:amd64.
Preparing to unpack .../04-libtbb2_4.4~20160526-0ubuntu2_amd64.deb ...
Unpacking libtbb2:amd64 (4.4~20160526-0ubuntu2) ...
Selecting previously unselected package libopencv-core2.4v5:amd64.
Preparing to unpack .../05-libopencv-core2.4v5_2.4.9.1+dfsg1-2_amd64.deb ...
Unpacking libopencv-core2.4v5:amd64 (2.4.9.1+dfsg1-2) ...
Selecting previously unselected package libopencv-imgproc2.4v5:amd64.
Preparing to unpack .../06-libopencv-imgproc2.4v5_2.4.9.1+dfsg1-2_amd64.deb ...
Unpacking libopencv-imgproc2.4v5:amd64 (2.4.9.1+dfsg1-2) ...
Selecting previously unselected package libpostproc54:amd64.
Preparing to unpack .../07-libpostproc54_7%3a3.2.4-1build2_amd64.deb ...
Unpacking libpostproc54:amd64 (7:3.2.4-1build2) ...
Selecting previously unselected package librubberband2v5:amd64.
Preparing to unpack .../08-librubberband2v5_1.8.1-6ubuntu2_amd64.deb ...
Unpacking librubberband2v5:amd64 (1.8.1-6ubuntu2) ...
Selecting previously unselected package libavfilter6:amd64.
Preparing to unpack .../09-libavfilter6_7%3a3.2.4-1build2_amd64.deb ...
Unpacking libavfilter6:amd64 (7:3.2.4-1build2) ...
Selecting previously unselected package libopenal-data.
Preparing to unpack .../10-libopenal-data_1%3a1.17.2-4_all.deb ...
Unpacking libopenal-data (1:1.17.2-4) ...
Selecting previously unselected package libopenal1:amd64.
Preparing to unpack .../11-libopenal1_1%3a1.17.2-4_amd64.deb ...
Unpacking libopenal1:amd64 (1:1.17.2-4) ...
Selecting previously unselected package libsdl2-2.0-0:amd64.
Preparing to unpack .../12-libsdl2-2.0-0_2.0.5+dfsg1-2ubuntu3_amd64.deb ...
Unpacking libsdl2-2.0-0:amd64 (2.0.5+dfsg1-2ubuntu3) ...
Selecting previously unselected package libavdevice57:amd64.
Preparing to unpack .../13-libavdevice57_7%3a3.2.4-1build2_amd64.deb ...
Unpacking libavdevice57:amd64 (7:3.2.4-1build2) ...
Selecting previously unselected package ffmpeg.
Preparing to unpack .../14-ffmpeg_7%3a3.2.4-1build2_amd64.deb ...
Unpacking ffmpeg (7:3.2.4-1build2) ...
Selecting previously unselected package subsonic.
Preparing to unpack .../15-subsonic-6.0.deb ...
Unpacking subsonic (6.0) ...
Setting up subsonic (6.0) ...
Setting up libavresample3:amd64 (7:3.2.4-1build2) ...
Processing triggers for ureadahead (0.100.0-19) ...
Setting up libebur128-1:amd64 (1.2.0-2) ...
Setting up libtbb2:amd64 (4.4~20160526-0ubuntu2) ...
Setting up libflite1:amd64 (2.0.0-release-3) ...
Setting up libopencv-core2.4v5:amd64 (2.4.9.1+dfsg1-2) ...
Setting up libopenal-data (1:1.17.2-4) ...
Setting up libbs2b0:amd64 (3.1.0+dfsg-2.2) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
Setting up libsdl2-2.0-0:amd64 (2.0.5+dfsg1-2ubuntu3) ...
Processing triggers for systemd (232-21ubuntu3) ...
Setting up libpostproc54:amd64 (7:3.2.4-1build2) ...
Processing triggers for man-db (2.7.6.1-2) ...
Setting up libopenal1:amd64 (1:1.17.2-4) ...
Setting up librubberband2v5:amd64 (1.8.1-6ubuntu2) ...
Setting up libopencv-imgproc2.4v5:amd64 (2.4.9.1+dfsg1-2) ...
Setting up libavfilter6:amd64 (7:3.2.4-1build2) ...
Setting up libavdevice57:amd64 (7:3.2.4-1build2) ...
Setting up ffmpeg (7:3.2.4-1build2) ...
Processing triggers for libc-bin (2.24-9ubuntu2) ...
```

---

### Post by #&amp;thj^% on 2017-05-12
> **hilario_ferreira said:**
> I get the same :file or directory not found

Very odd:confused:
```
cd Downloads && sudo dpkg -i subsonic-6.0.deb
[sudo] password for me: 
(Reading database ... 333919 files and directories currently installed.)
Preparing to unpack subsonic-6.0.deb ...
Unpacking subsonic (6.0) over (6.0) ...
Setting up subsonic (6.0) ...
Processing triggers for systemd (229-4ubuntu17) ...
Processing triggers for ureadahead (0.100.0-19) ...


```

```
$ apt search subsonic
Sorting... Done
Full Text Search... Done
subsonic/now 6.0 all [installed,local]
  A web-based music streamer, jukebox and Podcast receiver

xfoil/xenial 6.99.dfsg-2 amd64
  program for the design and analysis of subsonic airfoils


```
Try howefield's method then

---

### Post by ajgreeny on 2017-05-12
Or firstly install gdebi with ```
sudo apt-get install gdebi
``` then right click on your subsonic .deb file and choose to open it with gdebi.

Using dpkg can sometimes throw errors about missing dependencies but gdebi will deal with all of those and install anything missing as long as they are available in the repos you have enabled.

---

### Post by hilario_ferreira on 2017-05-12
> **ajgreeny said:**
> Or firstly install gdebi with ```
sudo apt-get install gdebi
``` then right click on your subsonic .deb file and choose to open it with gdebi.

Using dpkg can sometimes throw errors about missing dependencies but gdebi will deal with all of those and install anything missing as long as they are available in the repos you have enabled.

it worked that way.tks

---

### Post by ajgreeny on 2017-05-13
Great!
Please mark as solved from the Thread Tools menu at the top of the page. It is very helpful to users searching the forum for information.

---

