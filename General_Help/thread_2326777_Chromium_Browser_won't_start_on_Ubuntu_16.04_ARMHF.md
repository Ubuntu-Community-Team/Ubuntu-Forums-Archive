---
title: "Chromium Browser won't start on Ubuntu 16.04 ARMHF"
date: 2016-06-04
forum: General Help
---

### Post by The_Forgotten_King on 2016-06-04
I'm running Ubuntu 16.04 armhf on a Samsung ARM chromebook.
When I start chromium from the menu, nothing happens.
When I start it from a terminal, this happens:
```

[6856:6889:0604/123946:ERROR:zygote_host_impl_linux.cc(162)] Failed to adjust OOM score of renderer with pid 6947: Permission denied
[6856:6889:0604/123947:ERROR:zygote_host_impl_linux.cc(162)] Failed to adjust OOM score of renderer with pid 6971: Permission denied
[6856:6889:0604/123947:ERROR:zygote_host_impl_linux.cc(162)] Failed to adjust OOM score of renderer with pid 6974: Permission denied
[6856:6889:0604/123947:ERROR:zygote_host_impl_linux.cc(162)] Failed to adjust OOM score of renderer with pid 6979: Permission denied
[6856:6889:0604/123947:ERROR:zygote_host_impl_linux.cc(162)] Failed to adjust OOM score of renderer with pid 6981: Permission denied
[6917:6917:0604/123948:ERROR:sandbox_linux.cc(334)] InitializeSandbox() called with multiple threads in process gpu-process

```
Seeing "Permission Denied", I ran sudo chromium-bowser. This happens: 
```

[1:1:0604/124135:FATAL:setuid_sandbox_client.cc(126)] Check failed: IsFileSystemAccessDenied(). 
#0 0x0000b5691e1a base::debug::StackTrace::StackTrace()
#1 0x0000b56a3f12 logging::LogMessage::~LogMessage()
#2 0x0000b1eff2ae sandbox::SetuidSandboxClient::ChrootMe()
#3 0x0000b3cc2434 <unknown>
#4 0x0000b3a74d56 <unknown>
#5 0x0000b3a752c8 <unknown>
#6 0x0000b3a74af2 content::ContentMain()
#7 0x0000b5a3bbbc <unknown>
#8 0x0000b0a4e8aa __libc_start_main

Received signal 6
#0 0x0000b5691e1a base::debug::StackTrace::StackTrace()
#1 0x0000b5692104 <unknown>
#2 0x0000b0a5d260 <unknown>
#3 0x0000b0a4eaf6 <unknown>
#4 0x0000b0a5c638 gsignal
#5 0x0000b0a5d33a abort
[end of stack trace]

```

Any help?

---

### Post by The_Forgotten_King on 2016-06-05
Bumpedy Bump.

---

### Post by The_Forgotten_King on 2016-06-06
another one

---

### Post by hwertz10 on 2016-10-27
There's a bug open for it...
[https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1563184](https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/1563184)
     
Unfortunately, the short of it is chromium is quite complicated to build, to debug, and to even find out what causes a particular crash, and it looks like the cause of the crash is unknown.  In particular, it's hard to debug heavily threaded apps, and chromium uses lots of threads; they've found from the stack traces chromium dumps that it's crashing due to some sanity check failing, the CAUSE happens earlier and is so far unknown; and it appears that chromium behaves enough differently under gdb (debugger) that they haven't found the cause by running it under the debugger.

I mainly use Firefox anyway... I'm running an Acer Chromebook 13 (Acer CB5-311, with a Tegra K1) with Ubuntu 16.04 (thank goodness I backed up the whole disk with rsync, it took a try or two to successfully upgrade form 14.04 and keep the nvidia driver for the K1.)   Just days ago (running 14.04 on the same system) the latest chromium (52 or 53...) was running alright.  

By googling, I found suggestions that something went wrong on Ubuntu 16.04 armhf with chromium 49.  Reportedly chromium 48 (or 45) from 16.04 works; there's a build for raspbian (chromium 51) that works.  Also reportedly current chromium (53 right now) but the Ubuntu 14.04.1 version works.  I found for me they *didn't* quite work; they would open but then show "Aw, snap!" on all pages (including the chromium preferences and such.) edit:  They do work with a runtime flag.

Long story short:
I retrieved these files:
chromium-browser_53.0.2785.143-0ubuntu0.14.04.1.1142_armhf.deb
chromium-browser-l10n_53.0.2785.143-0ubuntu0.14.04.1.1142_all.deb
chromium-codecs-ffmpeg-extra_53.0.2785.143-0ubuntu0.14.04.1.1142_armhf.deb
(These are just current chromium for 14.04).  I ran 
"sudo dpkg -i chromium*53*14.04.1*.deb" to install these 3.
I edited /etc/chromium-browser/default and changed the last line to 

edit: 'CHROMIUM_FLAGS="--disable-namespace-sandbox"'
or (to get Flash going)
CHROMIUM_FLAGS="--disable-namespace-sandbox --ppapi-flash-path=/usr/lib/chromium-browser/plugins/libpepflashplayer.so"
     (And make sure libpepflashplayer.so is in /usr/lib/chromium-browser/plugins/).

I ran 
"sudo apt-mark hold chromium-browser chromium-codecs-ffmpeg-extra chromium-browser-l10n"
otherwise Ubuntu will replace the chromium with the 16.04 version next time you update.

If you want to undo this, run
"sudo apt-mark unhold chromium-browser chromium-codecs-ffmpeg-extra chromium-browser-l10n" 
and Ubuntu will update chromium next time you run updates (or tell it then to install chromium-browser and it'll get the new one); you can then change the last line of /etc/chromium-browser/default back to ' CHROMIUM_FLAGS="" '  (i.e. make it empty.)


I also found that the firefox plugin browser-plugin-freshplayer-pepperflash worked fine; I installed it, when I went to load a flash page it printed a message saying it looked in about a dozen locations for libpepperflash.so (and I didn't have it in any of them.)  So I copied it to /usr/lib/chromium-browser/PepperFlash/ and off it went.

---

