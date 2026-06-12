---
title: "Mplayer not working"
date: 2013-09-28
forum: General Help
---

### Post by CkDGTAT on 2013-09-28
Hi,

```
[~]% mplayer beep.mp3                  [git][jean/.][masterU]
MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing beep.mp3.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Audio only file format detected.
Clip info:
 Title:
 Artist:
 Album:
 Year:
 Comment:
 Genre: Other
Load subtitles in ./
==========================================================================
Trying to force audio codec driver family mp3lib...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   0.3 (00.3) of 0.7 (00.6)  0.4%




Exiting... (End of file)

```

Thanks

---

### Post by gordintoronto on 2013-09-29
Can you play other mp3 files? What version of Ubuntu? Can you play beep.mp3 in VLC Media Player? Where did beep.mp3 come from? Did you install the Restricted Extras?

---

### Post by CkDGTAT on 2013-10-06
1. I cannot play any other mp3
2. 12.04
3. Work with vlc

What would be the restricted Extras

```

p   gnome-mplayer                                                                               - A GTK+ interface for MPlayer                                                                         p   gnome-mplayer:i386                                                                          - A GTK+ interface for MPlayer                                                                         
p   gnome-mplayer-dbg                                                                           - A GTK+ interface for MPlayer (debugging symbols)                                                     
p   gnome-mplayer-dbg:i386                                                                      - A GTK+ interface for MPlayer (debugging symbols)                                                     
i   kmplayer                                                                                    - media player for KDE                                                                                 
p   kmplayer:i386                                                                               - media player for KDE                                                                                 
c   mplayer                                                                                     - movie player for Unix-like systems                                                                   
p   mplayer:i386                                                                                - movie player for Unix-like systems                                                                   
p   mplayer-dbg                                                                                 - debugging symbols for MPlayer                                                                        
p   mplayer-dbg:i386                                                                            - debugging symbols for MPlayer                                                                        
p   mplayer-doc                                                                                 - documentation for MPlayer                                                                            
p   mplayer-fonts                                                                               - Fonts for mplayer                                                                                    
p   mplayer-gui                                                                                 - movie player for Unix-like systems                                                                   
p   mplayer-gui:i386                                                                            - movie player for Unix-like systems                                                                   
v   mplayer-skin                                                                                -                                                                                                      
p   mplayer-skin-blue                                                                           - Transitional package for the 'blue' mplayer-skin package                                             
p   mplayer-skins                                                                               - Skins for the Mplayer package                                                                        
i   mplayer2                                                                                    - next generation movie player for Unix-like systems                                                   
p   mplayer2:i386                                                                               - next generation movie player for Unix-like systems                                                   
p   mplayer2-dbg                                                                                - Debugging symbols for mplayer2                                                                       
p   mplayer2-dbg:i386                                                                           - Debugging symbols for mplayer2                                                                       
p   mplayerthumbs                                                                               - video thumbnail generator using mplayer                                                              
p   mplayerthumbs:i386                                                                          - video thumbnail generator using mplayer                                                              
p   python-templayer                                                                            - layered template library for Python                                                                  
v   python2.7-templayer                                                                         -                                                                                                      
p   remuco-mplayer                                                                              - duplex remote control for media players - MPlayer adapter                                            
i   smplayer                                                                                    - complete front-end for MPlayer                                                                       
p   smplayer:i386                                                                               - complete front-end for MPlayer                                                                       
i A smplayer-themes                                                                             - complete front-end for MPlayer - icon themes                                                         
i A smplayer-translations                                                                       - complete front-end for MPlayer - translation files                                                   
p   vdr-plugin-mplayer                                                                          - MPlayer playback plugin for VDR                                                                      
p   vdr-plugin-mplayer:i386                                                                     - MPlayer playback plugin for VDR  
```

---

### Post by CkDGTAT on 2013-10-08
Reinstalling mplayer allows to load the proper codec, but still nothing

> MPlayer svn r34540 (Ubuntu), built with gcc-4.6 (C) 2000-2012 MPlayer Teammplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing preview.mp3.
libavformat version 53.21.1 (external)
Mismatching header version 53.19.0
Audio only file format detected.
Load subtitles in ./
==========================================================================
Trying to force audio codec driver family mp3lib...
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 48.0 kbit/3.40% (ratio: 6000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   2.8 (02.8) of 408.0 (06:48.0)  0.4%




MPlayer interrupted by signal 2 in module: play_audio
A:   3.0 (02.9) of 408.0 (06:48.0)  0.4%


Exiting... (Quit)




---

### Post by SeijiSensei on 2013-10-08
> **CkDGTAT said:**
> What would be the restricted Extras

Read: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

MP3 is patented and not distributed with stock Ubuntu.

---

