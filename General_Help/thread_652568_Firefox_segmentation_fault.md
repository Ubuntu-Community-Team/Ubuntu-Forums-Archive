---
title: "Firefox segmentation fault"
date: 2007-12-28
forum: General Help
---

### Post by sixsidepentagon on 2007-12-28
So my Firefox has been closing randomly. I can be certain, but I don't think it happened when I was using ol' Feisty (I've got Gusty right now).
My Firefox version is 2.0.0.11
It used to always fail randomly or when I tried to download a file, but I uninstalled and reinstalled, and now it only closes randomly. I tried turning off all of my extensions, and adding them one by one, but it turns out that it faults without any extensions at all.
The error message from the terminal is "Segmentation fault (core dumped)". I've been snooping around, and this seems like a fairly common error.
Would switching to Iceweasel, Swiftweasel, or Swiftfox correct the issue? And for that matter, what in God's name is the difference between them?
I've read that it probably is due to some sort of a memory problem. Does that mean a hardware problem? If not, how do I check for this?
So, if you have anything that my foolish newbie brain forgot to check for, please rudely inform me.

Thanks in advance,
Sixside.

---

### Post by sixsidepentagon on 2007-12-28
And I don't know if it matters, but I'm running Kubuntu.

---

### Post by xeth_delta on 2007-12-28
Try starting firefox from a terminal and see the errors shown on it when the browser crashes. you can post them here.

---

### Post by sixsidepentagon on 2007-12-28
Yeah, I already did that.

blah@blah:~$ : firefox
Segmentation fault (core dumped)

---

### Post by xeth_delta on 2007-12-28
What happens with
```
firefox -safe-mode
```

---

### Post by AllanM on 2008-01-13
Hi,

**firefox -safe-mode**

I´m having similar problems with FF 2.0.0.11 when browsing to:

[http://www.dodopad.com/tour/hall3.html](http://www.dodopad.com/tour/hall3.html)
then
[http://www.dodopad.com/tour/kitchen1.html](http://www.dodopad.com/tour/kitchen1.html)
(door bottom right)

seg faults like this:

allan@allan:~$ firefox -safe-mode
argn=src, argv=S-horse1.wav
argn=autostart, argv=false
argn=name, argv=sound1
argn=enablejavascript, argv=true
argn=height, argv=0
argn=width, argv=0
[00000001] main private debug: checking builtin modules
[00000001] main private debug: checking plugin modules
[00000001] main private debug: loading plugins cache file /home/allan/.vlc/cache/plugins-04041e.dat
[00000001] main private debug: recursively browsing `modules'
[00000001] main private debug: recursively browsing `/usr/lib/vlc'
[00000001] main private debug: recursively browsing `plugins'
[00000001] main private debug: module bank initialized, found 216 modules
[00000001] main private debug: opening config file /home/allan/.vlc/vlcrc
[00000001] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000001] main private debug: looking for memcpy module: 1 candidate
[00000001] main private debug: using memcpy module "memcpy"
[00000281] main playlist debug: waiting for thread completion
[00000281] main playlist debug: thread 2954361744 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000282] main private debug: waiting for thread completion
[00000282] main private debug: thread 2945969040 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000283] main interface debug: looking for interface module: 1 candidate
[00000283] main interface debug: using interface module "hotkeys"
[00000283] main interface debug: thread 2937551760 (interface) created at priority 0 (interface/interface.c:231)
[00000285] main interface debug: looking for interface module: 1 candidate
[00000285] main interface debug: using interface module "screensaver"
[00000285] main interface debug: thread 2929150864 (interface) created at priority 0 (interface/interface.c:231)
argn=src, argv=S-crash.wav
argn=autostart, argv=false
argn=name, argv=sound2
argn=enablejavascript, argv=true
argn=height, argv=0
argn=width, argv=0
[00000287] main private debug: translation test: code is "C"
[00000287] main private debug: module bank initialized, found 216 modules
[00000287] main private debug: opening config file /home/allan/.vlc/vlcrc
[00000287] main private debug: CPU has capabilities 486 586 MMX 3DNow! MMXEXT SSE SSE2 FPU 
[00000287] main private debug: looking for memcpy module: 1 candidate
[00000287] main private debug: using memcpy module "memcpy"
[00000289] main playlist debug: waiting for thread completion
[00000289] main playlist debug: thread 2920758160 (playlist) created at priority 0 (playlist/playlist.c:184)
[00000290] main private debug: waiting for thread completion
[00000290] main private debug: thread 2912365456 (preparser) created at priority 0 (playlist/playlist.c:210)
[00000291] main interface debug: looking for interface module: 1 candidate
[00000291] main interface debug: using interface module "hotkeys"
[00000291] main interface debug: thread 2903972752 (interface) created at priority 0 (interface/interface.c:231)
[00000292] main interface debug: looking for interface module: 1 candidate
[00000292] main interface debug: using interface module "screensaver"
[00000292] main interface debug: thread 2895580048 (interface) created at priority 0 (interface/interface.c:231)
[00000001] main private debug: removing all interfaces
[00000285] main interface debug: thread 2929150864 joined (interface/interface.c:258)
[00000285] main interface debug: removing module "screensaver"
[00000283] main interface debug: thread 2937551760 joined (interface/interface.c:258)
[00000283] main interface debug: removing module "hotkeys"
[00000001] main private debug: removing playlist handler
[00000282] main private debug: thread 2945969040 joined (playlist/playlist.c:247)
[00000281] main playlist debug: thread 2954361744 joined (playlist/playlist.c:248)
[00000001] main private debug: removing all video outputs
[00000001] main private debug: removing all audio outputs
[00000001] main private debug: removing module "memcpy"
Segmentation fault (core dumped)


(I´ve also had the runaway cpu problem as well)

This is on ubuntu 7.10 (fully up-to-date)

Allan.

---

