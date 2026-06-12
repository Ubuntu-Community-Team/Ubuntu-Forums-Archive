---
title: "Gimp locks up the entire system"
date: 2019-11-13
forum: General Help
---

### Post by vetmawd on 2019-11-13
Hey everybody. Couldn't find any answer to this on google/stackoverflow:

I'm running Ubuntu 19.10 with Gimp 2.10.12 on a Dell XPS 15 9550. For some reason when using Gimp, and ONLY when using Gimp my system randomly seems to freeze up entirely. I tried to check if it's from a specific action I do in Gimp but there is no pattern at all. My mouse will become unresponsive, so will my keyboard and the combinations to switch to TTY with ctrl + alt + F* keys won't work at all anymore. If I have a youtube video in the background, plex running or some music playing I can hear that still going though. So I guess it could be something with the graphics driver? But then why would the shortcut to drop back to TTY not work? The only thing I can do when this happens is REISUB.

Is there any way I can diagnose this problem and find the causing issue? It seems to happen with both nouveau and nvidia proprietary drivers. :(

---

### Post by SeijiSensei on 2019-11-13
How big are the images you're trying to edit? How much memory do you have, and do you have swap enabled?

---

### Post by sdsurfer on 2019-11-13
I would first open up the system monitor before launching Gimp and watch what's happening with memory and disk usage. I have an older hardware build due for a replacement with limited RAM, GIMP **limp**s along (pun intended) if I open too many files or large files.

---

### Post by oldrocker99 on 2019-11-13
Use this:
```
sudo apt install htop
```
This very useful utility is the old top command on steroids. It has easily-selectable between CPU and MEM, or other displays. It is the very easiest way to kill an errant process: F3 to find, F9 to kill, and select a kill command. I use 9, SIGKILL.

As someone else said, htop should be part of a standard installation in **every** distro. It's too farking useful not to have.
I usually open a console and run it, so that it's handy when all else fails (unless things are so bad that I can't open a console...).

---

### Post by vetmawd on 2019-11-14
> **SeijiSensei said:**
> How big are the images you're trying to edit? How much memory do you have, and do you have swap enabled?
They vary in size, it happens all the way from small ~200x200 sizes to 4k or larger. The freeze happens regardless.

I have 16gb RAM and swap is on:

$ cat /proc/meminfoMem
Total: 16210648 kB
MemFree: 10429196 kB
MemAvailable: 12350400 kB
Buffers: 204152 kB
Cached: 2198812 kB
SwapCached: 0 kB
Active: 3625412 kB
Inactive: 1469932 kB
Active(anon): 2745088 kB
Inactive(anon): 244904 kB
Active(file): 880324 kB
Inactive(file): 1225028 kB
Unevictable: 33588 kB
Mlocked: 32 kB
SwapTotal: 2097148 kB
SwapFree: 2097148 kB
Dirty: 1952 kB
Writeback: 0 kB
AnonPages: 2725824 kB
Mapped: 675328 kB
Shmem: 297616 kB
KReclaimable: 155064 kB
Slab: 358820 kB
SReclaimable: 155064 kB
SUnreclaim: 203756 kB
KernelStack: 17072 kB
PageTables: 55860 kB
NFS_Unstable: 0 kB
Bounce: 0 kB
WritebackTmp: 0 kB
CommitLimit: 10202472 kB
Committed_AS: 11477756 kB
VmallocTotal: 34359738367 kB
VmallocUsed: 58860 kB
VmallocChunk: 0 kB
Percpu: 8256 kB
HardwareCorrupted: 0 kB
AnonHugePages: 0 kB
ShmemHugePages: 0 kB
ShmemPmdMapped: 0 kB
CmaTotal: 0 kB
CmaFree: 0 kB
HugePages_Total: 0
HugePages_Free: 0
HugePages_Rsvd: 0
HugePages_Surp: 0
Hugepagesize: 2048 kB
Hugetlb: 0 kB
DirectMap4k: 667464 kB
DirectMap2M: 7536640 kB
DirectMap1G: 8388608 kB

> **sdsurfer said:**
> I would first open up the system monitor before launching Gimp and watch what's happening with memory and disk usage. I have an older hardware build due for a replacement with limited RAM, GIMP **limp**s along (pun intended) if I open too many files or large files.
Good idea. I'll give that a try but I'm posting this post first and edit the results in afterwards so I don't lose my typed text.

> **oldrocker99 said:**
> Use this:
```
sudo apt install htop
```
This very useful utility is the old top command on steroids. It has easily-selectable between CPU and MEM, or other displays. It is the very easiest way to kill an errant process: F3 to find, F9 to kill, and select a kill command. I use 9, SIGKILL.

As someone else said, htop should be part of a standard installation in **every** distro. It's too farking useful not to have.
I usually open a console and run it, so that it's handy when all else fails (unless things are so bad that I can't open a console...).
I agree, htop is awesome. Top just isn't quite the same. The problem is that once gimp freezes my entire machine freezes so there's no way for me to still use htop.

[B]Edit:
[/B]I was able to recreate the freeze with htop running. It didn't spike either RAM or CPU usage when it happened. In fact RAM never even went over 50% use even though I was doodling around on a 8k image. Any other ideas how I can find what's causing this?

---

### Post by ajgreeny on 2019-11-14
Just to be sure what we're dealing with, is this a snap version of gimp or is it the .deb version?

Let's see the output of command ***snap list*** in terminal.

---

### Post by vetmawd on 2019-11-14
> **ajgreeny said:**
> Just to be sure what we're dealing with, is this a snap version of gimp or is it the .deb version?

Let's see the output of command ***snap list*** in terminal.

I had it installed over snap at first but switched to deb version because I thought that snap might be responsible. Didn't help unfortunately.
Here you go:

$ snap list
Name                  Version                     Rev   Tracking  Publisher        Notes
chromium-ffmpeg       0.1                         15    stable    canonical&#10003;       -
code                  8795a988                    20    stable    vscode&#10003;          classic
core                  16-2.42.1                   8039  stable    canonical&#10003;       core
core18                20191030                    1265  stable    canonical&#10003;       base
gitkraken             6.3.1                       146   stable    gitkraken&#10003;       -
gnome-3-28-1804       3.28.0-16-g27c9498.27c9498  110   stable/…  canonical&#10003;       -
gnome-calculator      3.34.1+git1.d34dc842        544   stable/…  canonical&#10003;       -
gnome-characters      v3.32.1+git2.3367201        367   stable/…  canonical&#10003;       -
gnome-logs            3.34.0                      81    stable/…  canonical&#10003;       -
gnome-system-monitor  3.32.1-3-g0ea89b4922        111   stable/…  canonical&#10003;       -
gtk-common-themes     0.1-25-gcc83164             1353  stable/…  canonical&#10003;       -
gtk2-common-themes    0.1                         5     stable    canonical&#10003;       -
nmap                  7.80                        564   stable    maxiberta        -
opera                 64.0.3417.92                59    stable    opera-software&#10003;  -
pycharm-community     2019.2.4                    163   stable    jetbrains&#10003;       classic
sickgear              0.20.7                      503   stable    sickgear         -
sqlitebrowser         3.11.2-3092-6d2db6d         1709  edge      gajjgndu         -
strawberry            0.6.6+git                   2097  stable    jonaski          -
sublime-text          3211                        77    stable    snapcrafters     classic
vlc                   3.0.7                       1049  stable    videolan&#10003;        -
wire                  3.11.2912                   50    stable    snapcrafters     -

---

