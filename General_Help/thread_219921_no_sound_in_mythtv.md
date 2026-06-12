---
title: "no sound in mythtv"
date: 2006-07-20
forum: General Help
---

### Post by maino82 on 2006-07-20
i'm having problems with sound in mythtv and other multimedia applications. the system sounds work just fine, and i hear the typical ubuntu bongos on a regular basis, but but videos (from my harddrive or online) as well as live tv in mythtv do not produce any sound. i have tried configuring mythtv to use alsa (ALSA:default with default as the mixer) and have tried the mythtv defaults (/dev/dsp with /dev/mixer as the mixer) and neither of those have worked. in addition, i have tried setting the overall system sound settings  (system->preferences->multemdeia systems selector) in every combination possible, none of which had any effect. what could be causing the sound system to play regular system sounds but not other audio? below is some output from mythfrontend. nothing looks out of the ordinary to me (except that it fails to load lirc, which doesn't matter to me as i don't have a remote) but maybe someone else can spot something i missed. thanks!

> 2006-07-20 14:36:23.906 New DB connection, total: 1
Total desktop width=1280, height=1024, numscreens=1
2006-07-20 14:36:23.940 Using screen 0, 1280x1024 at 0,0
2006-07-20 14:36:23.961 mythfrontend version: 0.18.1.20050510-1 [www.mythtv.org](www.mythtv.org)
2006-07-20 14:36:23.962 Enabled verbose msgs : important general
2006-07-20 14:36:24.106 Switching to square mode (G.A.N.T.)
mythtv: could not connect to socket
mythtv: No such file or directory
lirc_init failed for mythtv, see preceding messages
2006-07-20 14:36:24.770 Joystick disabled.
2006-07-20 14:36:24.816 Registering Internal as a media playback plugin.
2006-07-20 14:36:24.827 Registering MythDVD DVD Media Handler as a media handler2006-07-20 14:36:24.931 Registering MythMusic Media Handler as a media handler
2006-07-20 14:36:30.317 New DB connection, total: 2
2006-07-20 14:36:30.340 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2006-07-20 14:36:30.346 Using protocol version 15
2006-07-20 14:36:30.372 Using protocol version 15
2006-07-20 14:36:30.699 Opening audio device '/dev/dsp'.
2006-07-20 14:36:30.699 Opening OSS audio device '/dev/dsp'.
2006-07-20 14:36:30.723 Using XV port 122
2006-07-20 14:36:30.969 Realtime priority would require SUID as root.
2006-07-20 14:36:30.996 Changing from None to WatchingLiveTV
2006-07-20 14:36:31.098 Video timing method: USleep with busy wait
2006-07-20 14:37:45.638 Changing from WatchingLiveTV to None
2006-07-20 14:37:45.647 Changing from None to None

---

