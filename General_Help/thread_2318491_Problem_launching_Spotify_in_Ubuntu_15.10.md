---
title: "Problem launching Spotify in Ubuntu 15.10"
date: 2016-03-26
forum: General Help
---

### Post by Emma_Ranger on 2016-03-26
Since upgrading to 15.10 a couple of weeks ago, we've been unable to launch Spotify - it opens, shows a blank screen then closes.  I've tried uninstalling and reinstalling, removing and adding the latest stable and development releases, as well as installing the relevant  libcrypt11 libraries.  When I run Spotify from terminal I get the following:

```

[0326/192531:ERROR:browser_main_loop.cc(203)] Running without the SUID sandbox! See https://code.google.com/p/chromium/wiki/LinuxSUIDSandboxDevelopment for more information on developing with the sandbox on.
[0326/192531:ERROR:main_delegate.cc(764)] Could not load cef_extensions.pak
[0326/192531:ERROR:main_delegate.cc(764)] Could not load cef_extensions.pak
19:25:32.354 5 [playlist_be_pl4_context.cpp:70  ] [spotify:user:1234:rootlist] Creating context
19:25:32.354 5 [playlist_be_pl4_context.cpp:70  ] [spotify:user:1234:publishedrootlist] Creating context
19:25:33.036 I [dns.cpp:63                      ] resolved apresolve.spotify.com to 194.132.197.198
19:25:33.037 I [dns.cpp:63                      ] resolved apresolve.spotify.com to 194.132.196.227
19:25:33.037 I [dns.cpp:63                      ] resolved apresolve.spotify.com to 194.132.198.198
19:25:34.090 I [ap_connection_impl.cpp:489      ] Connecting to AP lon3-accesspoint-a18.ap.spotify.com:4070
19:25:34.119 I [dns.cpp:63                      ] resolved lon3-accesspoint-a18.ap.spotify.com to 194.132.197.178
19:25:34.139 I [ap_connection_impl.cpp:139      ] Connected to AP: 194.132.197.178:4070
19:25:34.213 I [ap_connection_impl.cpp:337      ] AP login complete, len 0
19:25:50.284 D [gaia_manager.cpp:701            ] GAIA: TIMING(659122) GaiaManager::start, _service_status=kServiceStatusStopped
19:25:50.284 D [gaia_manager.cpp:1057           ] GAIA: TIMING(659122) GaiaManager::sendSubscribe
19:25:50.284 D [gaia_manager.cpp:360            ] GAIA: GaiaManager::stateTransition, kServiceStatusStopped->kServiceStatusInSubscribeTx
19:25:50.307 I [audio_driver_linux.cpp:20       ] Using PulseAudio
19:25:50.307 I [audio_player_queue_impl.cpp:410 ] Pause driver: 0x000010762d0c02d0
Segmentation fault (core dumped)

```

Any help would be greatly appreciated

Thanks

---

### Post by Emma_Ranger on 2016-04-10
bump

---

### Post by howefield on 2016-04-10
What version of spotify are you using ?

```
apt show spotify-client
```

Athough I have long since given up on the standalone client in favour of the web player @ play.spotify.com I installed and tried the testing version (Version: 1:1.0.27.71.g0a26e3b2-9) on this machine is running Ubuntu 15.10 which seems to work as intended.

---

### Post by Emma_Ranger on 2016-04-10
Hi, thanks for picking this up :-)

It looks like I have two versions, as when I run "apt show spotify-client" it tells me I have an additional record, so running with "-a" gives me version 1:1.0.26.125g64dc8bc6-14 and version 1:1.0.25.127 g58007b4c-22.

I'll give the testing version a go and see if that works

:D

---

### Post by howefield on 2016-04-10
Do purge what you have already installed first (both versions if indeed you have 2) :)

Just post back if you need it.

---

