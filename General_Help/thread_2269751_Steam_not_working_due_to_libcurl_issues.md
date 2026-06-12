---
title: "Steam not working due to libcurl issues"
date: 2015-03-17
forum: General Help
---

### Post by pNzKE6H on 2015-03-17
After fighting with my install for a few days, I was able to get everything fixed, my USB 3 is working, and I have installed the AMD Xorg edgers drivers without any issue. However, I was not aware that not installing Steam before you install the AMD drivers can cause quite the mess (at least this is what some research seems to suggest). Steam fails to open, here is the output:

```
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150317220823_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/crispy/.local/share/Steam/steam.sh: line 730:  2770 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
mv: cannot stat &#8216;/home/crispy/.steam/registry.vdf&#8217;: No such file or directory
Installing bootstrap /home/crispy/.local/share/Steam/bootstrap.tar.xz
Reset complete!
Restarting Steam by request...
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME has been set by the user to: /home/crispy/.local/share/Steam/ubuntu12_32/steam-runtime
Installing breakpad exception handler for appid(steam)/version(0_client)
Uploading dump (out-of-process) [proxy '']
/tmp/dumps/crash_20150317220834_1.dmp
Finished uploading minidump (out-of-process): success = no
error: libcurl.so: cannot open shared object file: No such file or directory
/home/crispy/.local/share/Steam/steam.sh: line 730:  2932 Segmentation fault      (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"

```

It can't access the shared object file for libcurl, likely because the 32 bit version did not install correctly. To be clear, the OS is 14.04 LTS 64 bit.



I have seen fixes online where you can purge gfx drivers, reboot, install steam, reboot, and install gfx drivers again. I was wondering if there is an easier fix, because I am hesitant to continue messing with the display driver.

I tried doing a package search for libcurl:i386 but that did not return anything.

---

### Post by pNzKE6H on 2015-03-19
Still having this problem. I have no idea what to do.

---

### Post by dino99 on 2015-03-19
you'd better expose that issue to steam devs

---

