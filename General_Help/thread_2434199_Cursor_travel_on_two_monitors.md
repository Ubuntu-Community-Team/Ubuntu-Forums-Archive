---
title: "Cursor travel on two monitors"
date: 2020-01-01
forum: General Help
---

### Post by kurt18947 on 2020-01-01
[FONT=Calibri]Hi All I&#8217;m hoping someone has some insight into my 2 monitor problem. First the setup &#8211; PC is a homebuilt, Asrock AB350M MoBo, Ryzen 3 2200G with Vega 8 graphics. It&#8217;s been working very well with one monitor running both X and Wayland.  Output from lspci:[/FONT]

 
 
 [FONT=Calibri]38:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Raven Ridge [Radeon Vega Series / Radeon Vega Mobile Series] (rev c8) (prog-if 00 [VGA controller])[/FONT]
 [FONT=Calibri]    Subsystem: Advanced Micro Devices, Inc. [AMD/ATI] Vega [Radeon Vega 8 Mobile][/FONT]
 [FONT=Calibri]    Flags: bus master, fast devsel, latency 0, IRQ 74[/FONT]
 [FONT=Calibri]    Memory at e0000000 (64-bit, prefetchable) [size=256M][/FONT]
 [FONT=Calibri]    Memory at f0000000 (64-bit, prefetchable) [size=2M][/FONT]
 [FONT=Calibri]    I/O ports at e000 [size=256][/FONT]
 [FONT=Calibri]    Memory at fe500000 (32-bit, non-prefetchable) [size=512K][/FONT]
 [FONT=Calibri]    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K][/FONT]
 [FONT=Calibri]    Capabilities: <access denied>[/FONT]
 [FONT=Calibri]    Kernel driver in use: amdgpu[/FONT]
 [FONT=Calibri]    Kernel modules: amdgpu[/FONT]
 
 
 [FONT=Calibri]I have the video memory allocation set to auto. I can set it to a fixed amount if that might help. I did install HWE for kernel and X.org, That was required to get onboard graphics to work in 18.04. [/FONT] 
 
 
 [FONT=Calibri]Now for my issue. When I first enabled all this I could move the cursor between screens by moving directly across the divide between the two screen when logged in using X. I had been experimenting with Wayland on a single monitor and it seemed to be working pretty reliably.  I tried Wayland on the two screen setup and the only way to move the cursor from one screen to another was to move the cursor off the edge of the monitor opposite where they meet (outboard edges). The cursor would disappear from one screen and onto the other. It&#8217;s a long ways to move the cursor though. Changing between X or Wayland with the attendant cursor movement worked a couple times, cursor would 'jump the gap'  but now I cannot move across the boundary between the two screens, I have to move off the outboard edge of one screen then the cursor appears on the outboard edge of the other screen.[/FONT]

 
 
 [FONT=Calibri]Does anyone have a thought about what changed so  the cursor refuses the &#8216;jump the gap&#8217; between the screens in X after working initially? I did load a live version of 19.10 and it behaved the same as current, I could not &#8216;jump the gap&#8217; between the screens, I had to run it off the outboard edge of one screen and onto the outboard edge of the other screen.  Apologies if this is too wordy, I did my best.


EDIT: I think I've answered my own question. The default when first installed is to make the left screen the primary with top bar and stuff. Due to physical setup I preferred the right screen being so made that change. It didn't like the right screen being primary. When I switched the left screen back to primary cursor travel is as I prefer it.
[/FONT]

---

