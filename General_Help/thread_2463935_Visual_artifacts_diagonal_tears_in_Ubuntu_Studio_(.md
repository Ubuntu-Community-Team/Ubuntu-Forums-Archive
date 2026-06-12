---
title: "Visual artifacts: diagonal tears in Ubuntu Studio (Plasma-related?)"
date: 2021-06-21
forum: General Help
---

### Post by burkingman on 2021-06-21
A few people have reported this elsewhere but I haven't found anything on this forum, so I'm documenting it here in case anybody might help. I'm running a basically fresh install of Ubuntu Studio (repartitioned my whole system drive, deleted all config files from my home partition except for a few application profiles). Most everything works smoothly, but as I type this, I can see pixels missing from the text cursor and from some of the forum interface. Such glitches become obvious when I highlight text (see screenshot below). I also get similar diagonal tears in certain icons in the application launcher.

[ATTACH=CONFIG]288709[/ATTACH]

I'm running Ubuntu Studio 21.04, with Plasma 5.21.4. Installed kernel was 5.11-0-16-lowlatency; I upgraded all packages and am now using the 5.11-0-18-lowlatency kernel and the problem is still present. Using integrated graphics (HD 2500) from an Intel i5-3570 processor. More tech details at the bottom of the post.

Here are some reports with identical symptoms:
[LIST]
[*][Artifacts in display on Kubuntu 20.10]("https://askubuntu.com/questions/1334681/artifacts-in-display-on-kubuntu-20-10") (on kernel 5.8.0-50-generic; apparently solved by downgrading the kernel) 
[*][Weird visual artifacts in Kubuntu 21.04]("https://www.reddit.com/r/Kubuntu/comments/nt2ixh/weird_visual_artifacts_in_kubuntu_2104/") (unsolved) 
[*][How do I fix these “diagonal tears” that appeared since I upgraded to 20.10?]("https://askubuntu.com/questions/1336650/how-do-i-fix-these-diagonal-tears-that-appeared-since-i-upgraded-to-20-10") (unsolved) 
[*][Highlight Diagonal Tears with Intel Graphics (Ubuntu 20.04)]("https://askubuntu.com/questions/1344765/highlight-diagonal-tears-with-intel-graphics-ubuntu-20-04") (unsolved; bounty offered) 
[/LIST]

All of these seem to be using integrated graphics on an Intel chip, and most are using Plasma. The first case seems to involve a kernel known to be faulty, but the one I'm using is newer.
So far, I've tried creating an Intel config file (/usr/share/X11/xorg.conf.d/20-intel.conf) to set DRI to 3 and AccelMethod to sna, which helped with some issues on my previous setup but has no effect on my current problem. Any ideas? I'll report back with any useful info.

inxi -F:
```
System:
  Host: [redacted] Kernel: 5.11.0-18-lowlatency x86_64 bits: 64 
  Desktop: KDE Plasma 5.21.4 Distro: Ubuntu 21.04 (Hirsute Hippo) 
Machine:
  Type: Desktop Mobo: ASUSTeK model: P8Z77-V LX v: Rev X.0x 
  serial: <superuser required> BIOS: American Megatrends v: 2501 
  date: 07/21/2014 
CPU:
  Info: Quad Core model: Intel Core i5-3570 bits: 64 type: MCP 
  L2 cache: 6 MiB 
  Speed: 1605 MHz min/max: 1600/3800 MHz Core speeds (MHz): 1: 1605 
  2: 1605 3: 1775 4: 1740 
Graphics:
  Device-1: Intel Xeon E3-1200 v2/3rd Gen Core processor Graphics 
  driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.11 driver: loaded: intel 
  resolution: 1680x1050~60Hz 
  OpenGL: renderer: Mesa DRI Intel HD Graphics 2500 (IVB GT1) 
  v: 4.2 Mesa 21.0.1 
Audio:
  Device-1: Intel 7 Series/C216 Family High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.11.0-18-lowlatency 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp3s0 state: up speed: 100 Mbps duplex: full 
  mac: 60:a4:4c:59:32:e7 
Drives:
  Local Storage: total: 1.93 TiB used: 1.24 TiB (64.3%) 
  ID-1: /dev/sda vendor: Western Digital model: WD20EARX-008FB0 
  size: 1.82 TiB 
  ID-2: /dev/sdb vendor: Samsung model: SSD 840 Series size: 111.79 GiB 
Partition:
  ID-1: / size: 99.92 GiB used: 11.81 GiB (11.8%) fs: ext4 dev: /dev/sdb1 
  ID-2: /home size: 953.78 GiB used: 641.96 GiB (67.3%) fs: ext4 
  dev: /dev/sda6 
Swap:
  Alert: No Swap data was found. 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 221 Uptime: 38m Memory: 7.46 GiB used: 2.82 GiB (37.8%) 
  Shell: Bash inxi: 3.3.01
```

---

### Post by burkingman on 2021-06-22
More info:
- the glitches seem to only appear in specific contexts: inside the Application Launcher, or when typing in the Info Center or System Settings, or in Firefox (within the page and within the Firefox interface). Many (most?) apps look OK: LibreOffice, GIMP, Kwrite, Konsole, Dolphin, VLC seem to display properly.
- I tried deactiving the compositor, then reactivating it with XRender as the rendering backend (instead of the default OpenGL 2.0). Didn't help. (Firefox scrolling works better with the compositor.)
- I deleted the xserver-xorg-video-intel package (and the Intel xorg config file I'd created), since the package description discourages its use for the "newer" Intel chips such as mine. Doesn't seem to make a difference.

The fact that this affects Firefox and some of the KDE system software, but not the average app, has to be a clue... Still looking into this.

---

### Post by burkingman on 2021-06-24
Update: some people with similar symptoms have reported OpenGL 3D glitches. [Here's a good example.]("https://askubuntu.com/questions/1332149/opengl-rendering-missing-some-triangles-why-and-how-to-fix") I get the same results with glxgears.

[Best answer I've seen so far]("https://askubuntu.com/questions/1336650/how-do-i-fix-these-diagonal-tears-that-appeared-since-i-upgraded-to-20-10") is that it is a kernel bug affecting Intel HD graphics, not limited to the 5.8.0-49 and 5.8.0.50 kernels, but present in later kernels as well, and fixed in 5.12.6. I may try to upgrade to the latest kernel in a few days to see if that solves the problem.

---

### Post by burkingman on 2021-10-13
Forgot to report back... Didn't need to use the latest kernel; it looks like the fix was backported to previous kernels. I think it was kernel 5.11.0.34 that fixed the problem for me. All good now; marking this topic solved.

---

