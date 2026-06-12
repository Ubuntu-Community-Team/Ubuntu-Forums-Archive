---
title: "Quicktime on Konqueror"
date: 2008-01-26
forum: General Help
---

### Post by Odd-rationale on 2008-01-26
Hello! I'm using Kubuntu 7.10 and I'm trying to get some quicktime to play on konqueror for school. I click in the quicktime link and I am assuming it opens it with KMplayer within Konqueror. All I get is a black screen. I right click the background and I can select between using xine and mplayer. If I use xine, I get this error:
> callback is konqueror-5624 KMPlayerCallback-4
trying video driver xv ..
trying audio driver alsa ..
play mrl: 'http://media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_03_04_02.mov'
XINE_EVENT_UI_PLAYBACK_FINISHED
event_finished
event_listener 7
request quit
closing display
done

If I use mplayer:
> MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.86GHz (Family: 6, Model: 13, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.
Resolving media.pearsoncmg.com for AF_INET6...
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Resolving media.pearsoncmg.com for AF_INET...
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
Cache size set to 128 KBytes
Cache fill:  2.52% (3306 bytes)   
Resolving media.pearsoncmg.com for AF_INET6...
Resolving media.pearsoncmg.com for AF_INET...
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
STREAM_ASF, URL: [http://media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_3_4_2_cc_MSTR.mov](http://media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_3_4_2_cc_MSTR.mov)
Resolving media.pearsoncmg.com for AF_INET6...
Server returned 404: Not Found
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Resolving media.pearsoncmg.com for AF_INET...
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
Resolving media.pearsoncmg.com for AF_INET6...
Server returned 404:Not Found
Failed to parse header.
Failed, exiting.
Resolving media.pearsoncmg.com for AF_INET...
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Resolving media.pearsoncmg.com for AF_INET6...
Server returned 404: Not Found
File not found: 'media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_3_4_2_cc_MSTR.mov'
Failed to open [http://media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_3_4_2_cc_MSTR.mov](http://media.pearsoncmg.com/ph/esm/esm_barnett_bcb11e_08/video/bcb11e_3_4_2_cc_MSTR.mov).
Resolving media.pearsoncmg.com for AF_INET...
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Cache size set to 128 KBytes
Cache fill:  0.00% (0 bytes)   No stream found.
Cache fill: 12.11% (15873 bytes)   
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
Resolving media.pearsoncmg.com for AF_INET6...
Couldn't resolve name for AF_INET6: media.pearsoncmg.com
Resolving media.pearsoncmg.com for AF_INET...
Connecting to server media.pearsoncmg.com[209.202.161.170]: 80...
Cache size set to 128 KBytes
Cache fill:  0.00% (0 bytes)   No stream found.
Cache fill: 12.11% (15874 bytes)   
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
Exiting... (End of file)

I have not a clue of what to do, so your help is greatly appreciated!

P.S. I can play .mov with kaffeine.

---

### Post by Whiffle on 2008-01-26
Mine is using kaffeine for embedded movies, i think there is an option in kaffeine somewhere.

---

### Post by knutschr on 2008-01-26
I'll recommand this excellent HowTo by  reassuringlyoffensive:
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by Odd-rationale on 2008-01-27
> **Whiffle said:**
> Mine is using kaffeine for embedded movies, i think there is an option in kaffeine somewhere.
Could you tell me how you do that? I can't figure it out.

Thanks!

[quote=knutschr] 
I'll recommand this excellent HowTo by reassuringlyoffensive:
 [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
[/quote]
Thanks for the link. I'll take a look. But I would hate to install realplayer if I didn;t have to...

---

