---
title: "Canon MF8280C not printing"
date: 2013-12-30
forum: General Help
---

### Post by rval001 on 2013-12-30
I purchased a Canon MF8280C laser printer for my wife.  It works great on her MAC and I can also use airprint without a problem.  I downloaded and installed the Linux driver from the Conan web site and installed both the common and ufr2 64bit deb files.  At one point I had the printer processing the file but never printed anything.  Currently I have reinstalled the cups print system and drivers and now it does nothing.

Output from the cups error log
W [30/Dec/2013:21:40:38 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8200C-UFRII-LT-Gray..' already exists
W [30/Dec/2013:21:40:38 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8200C-UFRII-LT-RGB..' already exists
W [30/Dec/2013:21:45:58 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8200C-UFRII-LT-Gray..' already exists
W [30/Dec/2013:21:45:58 -0500] CreateProfile failed: org.freedesktop.ColorManager.AlreadyExists:profile id 'Canon-MF8200C-UFRII-LT-RGB..' already exists
E [30/Dec/2013:21:46:17 -0500] [Job 54] src = bidiCommon.c, line = 1085, err = 0¥nDEBUG: Connecting to 192.168.1.230:9100

Any help would be greatly appreciated.

I should mention I am running Ubuntu 13.10 and connected to the printer via WLAN

---

