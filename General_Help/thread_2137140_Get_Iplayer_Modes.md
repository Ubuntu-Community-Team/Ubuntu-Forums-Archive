---
title: "Get_Iplayer Modes?"
date: 2013-04-19
forum: General Help
---

### Post by arsenic_creed on 2013-04-19
Hello,
My cousin wants to use the get_iplayer program but we can't get it to actually download anything. It installed without a problem and it brings up the information but whenever we try to use any of the commands all the tutorials we've seen use we get this notice:
```

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: No specified modes (default) available for this programme with version 'default' (try using --modes=)
ERROR: Failed to record 'imagine... - Summer 2010: 4. Tom Jones - What Good Am I? (b00t15v1)'

```
It does that no matter what the program is and regardless of what 'mode' is listed.
Thank you, pre-emptively, for any ideas you can offer.

---

### Post by arsenic_creed on 2013-04-19
It just occured to me that it might be of use for me to tell you that I've also run the '--info' and '--test' commands to see what modes were available and every show (even ones I saw people download without a problem in recent videos) simply listed 'default:' as the mode.

---

### Post by Cheesemill on 2013-04-20
Try this command followed by the shows PID. It's what I've always used without any problems (I have it set as an alias in my .bashrc file).

```
get_iplayer --nocopyright --output=/home/rob/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get 
```

---

### Post by arsenic_creed on 2013-04-20
I just tried that with three different, randomly selected programmes and I'm still getting the same error. (I'm not sure what you mean by the bit in parenthesis there. I'm still quite new to the more advanced linux stuff.)

---

### Post by Cheesemill on 2013-04-20
> **arsenic_creed said:**
> I'm not sure what you mean by the bit in parenthesis there. I'm still quite new to the more advanced linux stuff.

An alias is just a custom shortcut for a command. You set them up with (surprisingly enough) the alias command. For example I have these 2 aliases set up on my system...
```
alias ipl='get_iplayer --nocopyright'
alias gipl='get_iplayer --nocopyright --output=/home/rob/Videos --tvmode=flashhd,flashvhigh,flashhigh,flashstd,flashnormal --get'
```

I can now use these simple commands at the terminal instead of having to remember and type out the full versions. The ipl command will search for shows, and the gipl command will download a show in the highest available quality saving a transcoded .mp4 version in my Videos folder. For example...
```
rob@quantal:~$ ipl qi
Matches:
698:    QI: Series J - 11. Jumpers, BBC Two, Comedy,Entertainment,Games & Quizzes,Guidance,Popular,TV, default,

INFO: 1 Matching Programmes
rob@quantal:~$ 
rob@quantal:~$ 
rob@quantal:~$ 
rob@quantal:~$ gipl 698
Matches:
698:    QI: Series J - 11. Jumpers, BBC Two, Comedy,Entertainment,Games & Quizzes,Guidance,Popular,TV, default,

INFO: 1 Matching Programmes
INFO: Checking existence of default version
INFO: flashvhigh1,flashvhigh2,flashhigh1,flashhigh2,flashstd1,flashstd2 modes will be tried for version default
INFO: Trying flashvhigh1 mode to record tv: QI: Series J - 11. Jumpers
INFO: File name prefix = QI_Series_J_-_11._Jumpers_b01p5626_default                 
RTMPDump v2.4
(c) 2010 Andrej Stepanchuk, Howard Chu, The Flvstreamer Team; license: GPL
Connecting ...
INFO: Connected...
Starting download at: 0.000 kB
INFO: Metadata:
INFO:   duration              1774.29
INFO:   moovPosition          32.00
INFO:   width                 832.00
INFO:   height                468.00
INFO:   videocodecid          avc1
INFO:   audiocodecid          mp4a
INFO:   avcprofile            77.00
INFO:   avclevel              30.00
INFO:   aacaot                2.00
INFO:   videoframerate        25.00
INFO:   audiosamplerate       24000.00
INFO:   audiochannels         2.00
INFO: trackinfo:
INFO:   length                44355000.00
INFO:   timescale             25000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            avc1
INFO:   length                42583040.00
INFO:   timescale             24000.00
INFO:   language              eng
INFO: sampledescription:
INFO:   sampletype            mp4a
325480.019 kB / 1774.25 sec (99.9%)
Download complete
ffmpeg version 0.8.6-6:0.8.6-0ubuntu0.12.10.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:16 with gcc 4.7.2
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[flv @ 0x1579ba0] Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from '/home/rob/Videos/QI_Series_J_-_11._Jumpers_b01p5626_default.partial.mp4.flv':
  Metadata:
    moovPosition    : 32
    avcprofile      : 77
    avclevel        : 30
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
  Duration: 00:29:34.29, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (Main), yuv420p, 832x468 [PAR 117:117 DAR 16:9], 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 48000 Hz, stereo, s16
Output #0, mp4, to '/home/rob/Videos/QI_Series_J_-_11._Jumpers_b01p5626_default.partial.mp4':
  Metadata:
    moovPosition    : 32
    avcprofile      : 77
    avclevel        : 30
    aacaot          : 2
    videoframerate  : 25
    audiochannels   : 2
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 832x468 [PAR 117:117 DAR 16:9], q=2-31, 25 tbn, 25 tbc
    Stream #0.1: Audio: libvo_aacenc, 48000 Hz, stereo
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
frame=44355 fps=12947 q=-1.0 Lsize=  325154kB time=1774.20 bitrate=1501.3kbits/s    
video:303405kB audio:20518kB global headers:0kB muxing overhead 0.380169%
INFO: Recorded /home/rob/Videos/QI_Series_J_-_11._Jumpers_b01p5626_default.mp4

INFO: Downloaded Thumbnail to '/home/rob/Videos/QI_Series_J_-_11._Jumpers_b01p5626_default.jpg'
INFO: MP4 tagging MP4 file

 Started writing to temp file.
 Progress: ===========================================================================>100%|
 Finished writing to temp file.
rob@quantal:~$ 
```
You can set aliases permanently by adding them to your users ~/.bashrc file


One thing I just want to check, you are attempting this from the UK aren't you?

---

