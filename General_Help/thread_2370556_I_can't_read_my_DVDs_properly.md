---
title: "I can't read my DVDs properly"
date: 2017-09-04
forum: General Help
---

### Post by chief096 on 2017-09-04
Hi, I've an issue on my Xubuntu 17.04 regarding the play of DVDs, that doesn't work properly. First of all I searched on the web and, as suggested, I've tried to install ubuntu restricted extras with: ```
sudo apt-get install ubuntu-restricted-extras
``` but without results. So then I've tried the command ```
sudo apt-get install libdvd-pkg
``` and ```
sudo dpkg-reconfigure libdvd-pkg
``` Now it seemed that works, but with a lot of issues again. First of all sometimes the play crashes on menus and then, if I try to select a particular instant during the play (so moving time cursor), it still crashes. The problems appear both in NTSC and PAL and are not related with DVD's region or player.

---

### Post by Autodave on 2017-09-05
What program are you using to play the DVD? I have found that VLC gives me the least trouble.

---

### Post by chief096 on 2017-09-05
I've tried with VLC and Parole Media Player. Both gave me issues

---

### Post by BenginM on 2017-09-05
Hiya , I have no issues playin' DVDs in Parole & VLC
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

run either players in terminal and try to play the same dvds and see what the logs have to say!

---

### Post by BenginM on 2017-09-05
Also, worth checkin' after the dvd is mounted play it then run $ dmesg , and look for messages and errors with lines starts with "sr "

for instance , when i insert Stuart little dvd , you could hear the disk spinning for sometime, but it doesn't play, and dmesg shows:

```


[170164.393667] sr 1:0:0:0: [sr0] tag#11 FAILED Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[170164.393679] sr 1:0:0:0: [sr0] tag#11 Sense Key : Illegal Request [current] 
[170164.393688] sr 1:0:0:0: [sr0] tag#11 Add. Sense: Logical block address out of range
[170164.393699] sr 1:0:0:0: [sr0] tag#11 CDB: Read(10) 28 00 00 38 b0 00 00 00 01 00
[170164.393706] blk_update_request: I/O error, dev sr0, sector 14860288
[170164.393721] Buffer I/O error on dev sr0, logical block 3715072, async page read


```

Also check if you can read (music) CDs, and check whether the DVD is '+' or '-', etc. Basically, is the issue the same for **any CD or DVD**, or certain (copy protected) ones? *Newer DVDs have 'updated' DRM and may still be unreadable on Ubuntu.* Perhaps try the DVDs in a PS4 (or similar) or 'DVD player', to eliminate the disc as the problem.

---

### Post by deadflowr on 2017-09-06
Do you have any non-restricted dvds to try out?
Just to see if it's a restricted playback problem or dvd playback problem in general. 

Like, home movies are usually good to test out non-restricted playback.
(versus a hollywood movie dvd, which most likely would be restricted)

---

### Post by chief096 on 2017-09-06
If previously I was capable to read something of my DVDs (for example at least the main menu), now nothing. There is the output of VLC: 

```
libdvdnav: Using dvdnav version 5.0.3libdvdnav: DVD Title: Critters3
libdvdnav: DVD Serial Number: 326869a4
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 2
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002780
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00002780)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00005dfa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00005dfa)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000e494
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000e494)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001bec6a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001bec6a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001bec8e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001bec8e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001d708d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001d708d)!!
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 2
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Invalid IFO for title 2 (VTS_02_0.BUP).
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Invalid IFO for title 2 (VTS_02_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1959121
libdvdread: Can't seek to block 1959121
libdvdread: Can't seek to block 1959121
libdvdread: Invalid IFO for title 4 (VTS_04_0.BUP).
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
[086c3d60] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).
[086c3d60] dvdread demux error: fatal error in vts ifo
[086c3d60] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[086c05f0] core input error: open of `dvd:///dev/sr0' failed
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: Critters3
libdvdnav: DVD Serial Number: 326869a4
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012a
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00002780
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_01_1.VOB (0x00002780)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x00005dfa
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x00005dfa)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x0000e494
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x0000e494)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x001bec6a
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_0.VOB (0x001bec6a)
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x001bec8e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_03_1.VOB (0x001bec8e)!!
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x001d708d
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_04_1.VOB (0x001d708d)!!
libdvdread: Elapsed time 0
libdvdread: Found 4 VTS's
libdvdread: Elapsed time 0
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Invalid IFO for title 2 (VTS_02_0.BUP).
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 24028
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Can't seek to block 1829954
libdvdread: Invalid IFO for title 2 (VTS_02_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1829984
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Can't seek to block 1929340
libdvdread: Invalid IFO for title 3 (VTS_03_0.BUP).
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1929350
libdvdread: Can't seek to block 1959121
libdvdread: Can't seek to block 1959121
libdvdread: Can't seek to block 1959121
libdvdread: Invalid IFO for title 4 (VTS_04_0.BUP).
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Invalid IFO for title 1 (VTS_01_0.IFO).
libdvdnav: ifoOpenVTSI failed
[b3e07178] dvdnav demux error: cannot set title (can't decrypt DVD?)
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 10106
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Can't seek to block 24022
libdvdread: Invalid IFO for title 1 (VTS_01_0.BUP).
[b3e07178] dvdread demux error: fatal error in vts ifo
[b3e07178] dvdread demux error: DvdReadSetArea(0,0,1) failed (can't decrypt DVD?)
[08693718] core input error: open of `dvd:///dev/sr0' failed

```

These DVDs, in a Windows equiped machine or in another player (like Xbox 360) work

---

### Post by mc4man on 2017-09-06
In regards to the critters3 - 
all those unable to crack keys would be an issue.
Try this - 
Put that dvd in drive, let drive settle, close out any pop ups.
Open home folder > show hidden files > delete the .dvdcss folder (must do this..

Open a terminal & run 
```
export DVDCSS_METHOD=title && export DVDCSS_VERBOSE=2
```
```
vlc dvd:// > vlc_output.txt 2>&1
```

See what happens, if it doesn't play (50-50) then in home folder find vlc_output.txt & attach to post (if too big then compress to a .gz & attach..

---

### Post by chief096 on 2017-09-06
I can do this with any DVD that shows me the same output?

---

### Post by chief096 on 2017-09-06
Now, I tried to play another DVD that showed me the same output of the previous one, but now it works without a reason (despite some glitches in the main menu). Now I'll attach the output of the terminal during the play 

```
** (vlc:4040): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-3hN7ITKC9S: Connection refusedlibdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: THE_HULK
libdvdnav: DVD Serial Number: 2f2a2847
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001f3de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00034fd4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003869c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003869c7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003dd211
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003dd216
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003dd22d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003dd232
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003df8be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003df8c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e13e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e13ec
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[9ef6e020] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[9efc4638] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[9efc4638] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
[b3e070d8] core input error: ES_OUT_RESET_PCR called
libdvdnav: Using dvdnav version 5.0.3
libdvdnav: DVD Title: THE_HULK
libdvdnav: DVD Serial Number: 2f2a2847
libdvdnav: DVD Title (Alternative): 
libdvdnav: DVD disk reports itself with Region mask 0x00fd0000. Regions: 2


libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient


libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x000001b9
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x0001f3de
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x00034fd4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003869c2
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003869c7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_0.VOB at 0x003dd211
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_03_1.VOB at 0x003dd216
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_0.VOB at 0x003dd22d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_04_1.VOB at 0x003dd232
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_0.VOB at 0x003df8be
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_05_1.VOB at 0x003df8c3
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_0.VOB at 0x003e13e7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_06_1.VOB at 0x003e13ec
libdvdread: Elapsed time 0
libdvdread: Found 6 VTS's
libdvdread: Elapsed time 0
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[975cba10] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: INPUT_CONTROL_SET_POSITION(_OFFSET) 9,4% failed
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[975cba10] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 423 ms)
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[975c9ab0] avcodec decoder: Using NVIDIA VDPAU Driver Shared Library  340.102  Mon Jan 16 12:24:40 PST 2017 for hardware decoding.
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
[b3e07210] core input error: ES_OUT_RESET_PCR called
QObject::~QObject: Timers cannot be stopped from another thread

```

However I'll not mark yet the thread as solved for now, because I don't understand why now it's working, and then I could have other problems. Do you see in this output something that could help you to understand the problem?

---

### Post by mc4man on 2017-09-06
Vlc terminal output is only useful to a point & it produces a lot of useless info so nothing there in last post. 
If things started working better after deleting the .dvdcss folder then you had corrupted or incorrect key files. 
Libdvdcss always uses the key files in its cache even if they are bad. 

In general one would not want to use the title method to decrypt as it can fail on very small titlesets, ie short extras, ect But in conjunction with dvdcss in debugging mode it can be useful. The exports I had mentioned are only active in the terminal instance run in.. 

As a side note: the time frame of that critters disk was during the heyday of structure protection, new line cinema was well-known to employ the most egregious they could find. Sometimes those disks can only be played on the main title only when using unlicensed players

---

### Post by BenginM on 2017-09-07
I wounder if changing the region to 1 would make a difference , i mean are these DVDs bought from a local store in europe? as it appears the disk is currently set to region 2.

  if they're from the US, then you can use regionset change and set it to region 1

$ sudo apt install regionset
$ regionset /dev/sr0 (where I assume your dvdplayer is /dev/sr0)
Remember that next time you cross continents.

---

### Post by chief096 on 2017-09-08
I don't need to change region, because I'm region 2. Furthermore I haven't deleted the .dvdcss folder but, despite this, now I can read my DVDs (I don't know why ;)). So now I can mark the thread as solved.

---

