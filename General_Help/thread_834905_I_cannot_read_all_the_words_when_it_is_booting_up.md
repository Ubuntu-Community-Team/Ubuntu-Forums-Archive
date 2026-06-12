---
title: "I cannot read all the words when it is booting up"
date: 2008-06-19
forum: General Help
---

### Post by danbar on 2008-06-19
I would like to read all that is written on my screen when it is booting up but it seems that the resolution is too big as I cannot read properly the words on the left and on the right.  When Ubuntu starts then everything is ok. I'm using a 19 inch ftp screen. The resolution that I normallly use is 1024 by 768.

Then when I'm switching off, the same problem. There a re lots of things written down but I cannot read all. 

Any solution?

---

### Post by sdennie on 2008-06-19
I'm not sure why you can't read the boot messages (though, if you are using a CRT monitor, it could be that you need to adjust the size of the screen for that resolution) but, after it boots you could type:

```

dmesg | more

```

That should show you all the information that was displayed at boot time.

---

### Post by danbar on 2008-06-19
This was the result.....(thanks for your time and patience)

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@vernadsky) (gcc version 4
.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 4 16:35:01 UTC 2008 (Ubuntu 2.6.24-
19.33-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ff40000 (usable)
[    0.000000]  BIOS-e820: 000000007ff40000 - 000000007ff50000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ff50000 - 0000000080000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] 1151MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 524096) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   524096
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
--More--

---

### Post by Lexicon101 on 2008-06-19
I found out recently that the login screen for gnome seems to use the first resolution defined in xorg-conf, mostly because I couldn't get 1080p output (still can't). I changed my resolution after logging in, but the login-screen is still a messed up 1080p.
(unless you were actually talking about the splash screen, which I know about nothing about.)

---

### Post by sdennie on 2008-06-19
Right.  If you keep hitting the spacebar, it should keep scrolling (and scrolling... and scrolling...).  You can also go to System->Administration->System Log and view the various system logs from there (including the startup information).

---

### Post by danbar on 2008-06-19
Right. If you keep hitting the spacebar, it should keep scrolling (and scrolling... and scrolling...). 

[COLOR="RoyalBlue"]there is no need to hit the spacebar as it keeps scrolling on its own. But I cannot read all the white letters on the black background![/COLOR]



You can also go to System->Administration->System Log and view the various system logs from there (including the startup information).

[COLOR="RoyalBlue"]Yes but I found an ocean of information.  What do I need to change?[/COLOR]

---

### Post by sdennie on 2008-06-20
> [COLOR="RoyalBlue"]Yes but I found an ocean of information.  What do I need to change?[/COLOR]

I'm not sure what you mean.  If you wanted to read the messages at bootup, they should all be in those logs.  If your monitor is not configured properly to read the startup information, hit Ctrl-Alt-F1 and use your monitors adjustment buttons to make sure all the information fits on the screen.  Once it's adjust hit Ctrl-Alt-F7 to return to the graphical interface.

---

### Post by danbar on 2008-06-20
I did fix it but then I tried to boot the problem came up again. It seems that it lost it's settings. 

The monitor is saying that it's out of range (the usual thing) when it's booting up.  Funnily enough when Ubuntu is running the screen is ok. 

Maybe I should use the system log if I need to look up for something.

---

### Post by sdennie on 2008-06-20
Strange that it doesn't work on reboot.  You could try changing the resolution of the boot screen: [https://wiki.ubuntu.com/FrameBuffer](https://wiki.ubuntu.com/FrameBuffer)

---

### Post by danbar on 2008-06-20
Thanks for your time and patience. I will look it up tomorrow.

---

