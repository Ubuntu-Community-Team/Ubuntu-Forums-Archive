---
title: "Steam not working?"
date: 2014-11-16
forum: General Help
---

### Post by th1mas on 2014-11-16
I recently installed steam on my Ubuntu 14.04 LTS installation. The program worked once, but now it won't even start. Even reinstalling it didn't work. I tried the solution posted in [this]("http://askubuntu.com/questions/345120/why-doesnt-steam-start") thread, but it still didn't work. This is the output when I start steam from the terminal.

> 
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20141116100102_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/thomas/.local/share/Steam/steam.sh: line 730: 11090 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat ‘/home/thomas/.steam/registry.vdf’: No such file or directory
Installing bootstrap /home/thomas/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/thomas/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20141116100106_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/thomas/.local/share/Steam/steam.sh: line 730: 11216 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"



---

