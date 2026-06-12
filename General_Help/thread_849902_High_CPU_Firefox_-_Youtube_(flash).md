---
title: "High CPU: Firefox - Youtube (flash)"
date: 2008-07-05
forum: General Help
---

### Post by Lan on 2008-07-05
High CPU when running Youtube (flash) on Firefox:

HighCPU about - Cpu(s): 83.0%us
This is when playing flash - ie. YouTube through Firefox

Still looking for solution -

DELL D810

Distributor ID: Ubuntu
Description: Ubuntu 8.04.1
Release: 8.04
Codename: hardy



Firefox: Mozilla/5.0 (X11;U;Linux i686;enUS;rv:1.9)Gecho/2008061015 Firefox/3.0

Installed Flash:
install_flash_player_9_linux.tar.gz



processor : 0
vendor_id : GenuineIntel
cpu family : 6
model : 13
model name : Intel(R) Pentium(R) M processor 2.00GHz
stepping : 8
cpu MHz : 1995.000
cache size : 2048 KB

MemTotal: 2075640 kB
MemFree: 1319220 kB
Buffers: 16568 kB
Cached: 344600 kB
SwapCached: 0 kB
Active: 473512 kB
Inactive: 199144 kB
HighTotal: 1179488 kB
HighFree: 514644 kB
LowTotal: 896152 kB





_____________________


Ok, issue resolved for me.

I don't exactly know how I fixed it but here's what I did.

Removed two flash that were associated with mozilla.
Didn't document it but if I can remember correctly:

libflash-mozplugin - GPL Flash (SWF) Library Mozilla compatible plugin
swfdec-mozilla - mozilla plugin for SWF (macromedia flash)

Also went to this site to check Flash Version:
It gave me this code WIN 9.100. - something like that which decodes as Windows and version 9.100
[http://www.mediacollege.com/adobe/flash/player/version/show.html](http://www.mediacollege.com/adobe/flash/player/version/show.html)

I also went here to DL and install this Flash Version:
[http://www.mediafire.com/?znhecmwx0j4](http://www.mediafire.com/?znhecmwx0j4)

Going back to that ShowFlashVersion site: Results to : LNX 9,0,124,0. It's no longer displaying WIN 9.100.xx.xx

Also installed flashplugin-nonfree

Everythings working good now. I'm ok with this Cpu(s): 35.9% than 85%

I'm not exactly sure which one of the steps corrected the issue.

BTW. before this issue was "corrected" there's a huge grey play button inside a huge circle (>) taking the whole youtube screen. You press that and it plays. It doesn't have that anymore.

Thanks.

---

