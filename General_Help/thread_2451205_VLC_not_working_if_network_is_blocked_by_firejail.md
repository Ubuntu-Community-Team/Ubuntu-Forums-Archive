---
title: "VLC not working if network is blocked by firejail?"
date: 2020-09-29
forum: General Help
---

### Post by dinkidonk on 2020-09-29
If I add "net none" to firejail's VLC profile, then VLC refuses to play any video/audio. The duration of the loaded media file is displayed in the time line, so it is recognized by VLC. When closing VLC after this failed attempt, VLC hangs indefinitely in the process list or until a KILL signal is sent to the process. Issue happens on fully updated Kubuntu 20.04, on 18.04 this does not happen.

Any workarounds for this issue?

---

### Post by TheFu on 2020-09-29
I suspect that vlc is using sockets between different processes to handle playback. You can check by using **lsof**.  This is common for Unix programs to use local network sockets as communications, since the difference between a local connection and an internet connection would simply be the IP address used, but there are vastly different security issues between using any 127.0.0.0/8 IP and all other IPs.

You may need to allow localhost networking in firejail for vlc to work. 
[https://unix.stackexchange.com/questions/478131/firejail-only-let-a-program-access-localhost](https://unix.stackexchange.com/questions/478131/firejail-only-let-a-program-access-localhost) appears to have a workable solution, but I didn't test it.

---

