---
title: "XFCE 14.04 - Chromium Browser fails to launch"
date: 2014-08-15
forum: General Help
---

### Post by 2CV67 on 2014-08-15
I upgraded my Xfce desktop machine from 13.10 to 14.04 a couple of days ago.
My normal browser is Firefox & that continues to work OK.
I only use Chromium occasionally, as a back-up & to use the translation facility.

The first time I tried to launch Chromium after the upgrade, I just got an error message saying it had closed unexpectedly.
Further attempts to launch give no result at all.
In fact, I hear a couple of seconds disk activity, but nothing on the screen.

I tried using SynApt to simply remove then reinstall Chromium - no change.

I then used SynApt to COMPLETELY remove Chromium, rebooted & reinstalled - no change.

I manually deleted the folder /.cache/Chromium and repeated the complete removal procedure - no change.

I notice that on reinstalling after COMPLETE removal, Synapt says zero B to be downloaded, which surprises me a little.

Any suggestions would be welcome.

Thanks!

---

### Post by JetStorm on 2014-08-15
Try running chromium through the terminal and paste the output here.
As for the zero bytes to be downloaded - apt probably already has the package in its local cache.

---

### Post by 2CV67 on 2014-08-15
> **JetStorm said:**
> Try running chromium through the terminal and paste the output here.
As for the zero bytes to be downloaded - apt probably already has the package in its local cache.

Thanks for your suggestion!
This is the result:
```
chris@Acer-desk:~$ apropos chromium
chromium-browser (1) - the web browser from Google
chris@Acer-desk:~$ chromium-browser
Illegal instruction (core dumped)
chris@Acer-desk:~$ 
```

I wondered if the local version might be corrupted & hoped that synapt would download a fresh one...

---

### Post by JetStorm on 2014-08-15
You can run **sudo apt-get clean** to clear the local cache then **sudo apt-get --purge remove chromium-package-name-here **(which will also remove all your settings)and finally **sudo apt-get install** **chromium-package-name-here** but i doubt it will fix the problem.
An alternative solution is to install the official Google Chrome package (you can check [**here**]("http://ubuntuforums.org/showthread.php?t=2238977") if you need help with the installation) and see what happens if you're not worried about their usage tracking.

And the final (and probably best) solution is to wait for someone else to give you a suggestion about the core dump error in the terminal.

---

### Post by 2CV67 on 2014-08-15
Thanks for the suggestions.

I am wondering if it is a hardware issue as my old Athlon is not SSE2-compatible.
Works with 13.10 & 12.04 though...

---

### Post by 2CV67 on 2014-08-15
Ah - this seems to be the problem:

> **32-bit systems predating SSE2**

As of version 35 of chromium, support for older hardware without an SSE2 instruction set has been removed upstream. Users of old hardware still wishing to use chromium may build the chromium-no-sse2 package or download a pre-compiled package from Repo-ck#Miscellaneous_packages. Keep in mind that requiring SSE2 fixed several bugs, and you should not report issues encountered with this patched version upstream. 
[https://wiki.archlinux.org/index.php/chromium](https://wiki.archlinux.org/index.php/chromium)

So that makes things more complicated...

---

### Post by 2CV67 on 2014-08-15
I went into Synapt, selected "chrome-browser" > Package > Force version.
I was offered 34.0 (no other choice) but that was previous to the v35 which stopped suporting my no-SSE2 hardware.
So I installed that.

It works!

So far...

---

