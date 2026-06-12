---
title: "smartdimmer doesn't work on 12.04"
date: 2012-12-01
forum: General Help
---

### Post by luxtux on 2012-12-01
Hi all,
I can't manage the brightness on my Sony Vaio FE21b.
On Ubuntu 11.04 I solved running smartdimmer, but now on Ubuntu 12.04 it doesn't work.

The terminal output is:
[I]smartdimmer -d
Errore di segmentazione (core dump creato)[/I]

and the crash report is:

[I]ExecutablePath
   /usr/bin/smartdimmer
Problem Type
   Crash
Title
   smartdimmer crashed with SIGSEGV
NonfreeKernelModules
   nvidia
SegvAnalysis
   Segfault happened at:0xb74a370a: movsb %sd:(%esi),%es:(%edi)
   PC (0xb74a370a) ok
   source "%sd:(%esi)" (0x0000007a) not located in know VMA region (needed readable region)!
   destination "%sd:(%esi)" (0x09c58203) ok
SegvReason
   reading NULL VMA
Signal
   11
SourcePackage
   nvclock
XsessionErrors
   gnome-session[1254]:WARNING:Session 'ubuntu' runnable check failed: Uscito con codice 1
   (gnome-settings-daemon:1309):color-plugin-WARNING**:failed to get edid:unable to get EDID for output
   (gnome-settings-daemon:1309):color-plugin-WARNING**:unable to get EDID for xrandr-default: unable to get EDID for output
   (gnome-settings-daemon:1309):color-plugin-WARNING**:failed to reset xrandr-default gamma tables:gamma size is zero[/I]

What does mean?
I haven't found any solution.. :(
Thx all

---

### Post by luxtux on 2012-12-04
Anybody can help me?

---

### Post by ajgreeny on 2012-12-16
Hi luxtux.

I would love to be able to help, but I don't really use 12.04 much (still on 10.04, Lucid for my main machine), and I don't have any experience of smartdimmer, nor problems with brightness on my old laptop where Lubuntu 12.04 works well.

I also have no idea about Sony machines, nor the hardware they use or the possible problems that may occur from using Ubuntu on them.

It seems to be a bit of a problem with that laptop judging by the search I just did at googlubuntu, so have a good long look through this link to see if anything helps there.
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Sony+Vaio+FE21b+brightness+smartdimmer&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Sony+Vaio+FE21b+brightness+smartdimmer&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

Good luck!

---

### Post by Pjotr123 on 2012-12-16
What's the output of:
```
lspci | grep -i vga
```

---

### Post by luxtux on 2012-12-18
Thanks ajgreenj, I'll try to find there..

The output is:
lspci | grep -i vga
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)

---

