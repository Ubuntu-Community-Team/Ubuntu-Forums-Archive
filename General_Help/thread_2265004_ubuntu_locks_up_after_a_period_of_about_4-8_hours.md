---
title: "ubuntu locks up after a period of about 4-8 hours"
date: 2015-02-11
forum: General Help
---

### Post by wriordan on 2015-02-11
hi everyone,
I recently switched to using ubuntu as my main OS on my home computer, i mainly use this pc for browsing the web and as a htpc so it does be switched on most of the time. The issue I'm having is that Ubuntu locks up every 4 or 8 hours after its switched on it seems to always happen after either one of those times. I've check the syslog and kernal log last night after it happened and this seems to be the only error i can find:
```

Feb 11 00:56:31 wayne-PCL kernel: [12922.247575] traps: kodi.bin[2287] general protection ip:7fe8a0fa1303 sp:7fff663a7b80 error:0 in libstdc++.so.6.0.19[7fe8a0f44000+e6000]

```
which i find wierd as it also happens when kodi isn't running any idea how i can resolve this issue.

---

### Post by TheFu on 2015-02-12
Which OS and version?

Generally, when a system locks up and doesn't leave any issues in the log files, that means hardware.  Check the RAM, PSU, GPU, and for overheating.

BTW, on my 14.04 x64 XMBC/Kodi/Plex box, I'm not seeing that message - or any kodi messages.

---

### Post by wriordan on 2015-02-12
That was my intial though that it was hardware but it runs windows fine i can leave it running for days when i boot into windows and it wont lock up. i also check the case for dust build up just in case its an overheating issue. Could it be a hardware compatibility issue and if so how do i find whats causing it.
edit: its 14.04 and just the standard desktop version

---

### Post by TheFu on 2015-02-12
Checking the log files for issues is the normal method.
Picking hardware known-to-work-well with Linux is the 2nd.

The normal way to look for hardware compatibility issues are:
* google every chip in the machine for issues
* setup monitoring for every temperature in the case, all fan speeds, etc.
* swap 1 component at a time until you determine which is causing the issue

Once you find the issue, please **write a polite** letter to the CEO of the vendor describing the issue and the amount of time you spent.  Don't expect much of a response besides thanks for writing and we support Windows.

---

### Post by wriordan on 2015-02-12
I installed some updates this morning and the issue seems to be resolved now as ubuntu hasn't locked up once in a 14 hour period. Not sure what caused it but it appears to fixed now.

---

### Post by TheFu on 2015-02-12
Staying patched with consistent software releases is very important.
[http://blog.jdpfu.com/linsysmaint](http://blog.jdpfu.com/linsysmaint) might be helpful for this minimal things to be done to maintain a Debian system.

---

