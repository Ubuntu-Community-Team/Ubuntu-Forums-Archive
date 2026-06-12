---
title: "Framebuffer console output shifted"
date: 2013-11-24
forum: General Help
---

### Post by rty2 on 2013-11-24
I found a few ancient (closed) threads which describe the same problem, but no solution.

**Problem**

While the X11 visualization is perfect, the high-res framebuffer console content (all consoles) is displayed shifted right+downwards:

```

+----------------------------------------+
+                                        +
+                                        +
+                                        +
+                     Ubuntu 12.04.3     +
+                     login:             +
+                                        +
+                                        +
+----------------------------------------+

```

The screen shows 64 rows, 160 columns (reported by [FONT=courier new]stty -a[/FONT]). A long line is somehow wrapped, although CR and LF appear to be sent at different times -- entering 160 times 'a' followed by 1 few 'b' would be displayed like this:

```

+----------------------------------------+
+                                        +
+aaaaaaaaaaaaaaaaaaaaa> aaaaaaaaaaaaaaaaa+
+                     bbbbbbbbbb         +
+                                        +
+----------------------------------------+

```

This problem appeared when upgrading from 10.04 to 12.04.3. With 10.04 everything was fine. No hardware was changed.

The display is connected via analog input, auto-adjust to the VGA sync signal didn't fix the problem.
[B]
System

[/B][TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]Computer[/TD]
[TD]Shuttle X27D[/TD]
[/TR]
[TR]
[TD]Graphics board[/TD]
[TD]AMD Radeon HD 6430M (Chipset = 0x6761)[/TD]
[/TR]
[TR]
[TD]Distro / Kernel[/TD]
[TD]Kubuntu 12.04.3 LTS / 3.2.0-56-generic #86[/TD]
[/TR]
[TR]
[TD]X.Org[/TD]
[TD]1.11.3 (2011-12-16)
driver fglrx 8.98.2 (2012-06-11)[/TD]
[/TR]
[TR]
[TD]Display[/TD]
[TD]Dell 1905 FP, analog input[/TD]
[/TR]
[TR]
[TD]Console settings[/TD]
[TD]1280*1024 @ 60Hz[/TD]
[/TR]
[/TABLE]

[B]Attempts to fix
[/B]
Activating grub2's config parameter [FONT=courier new]GRUB_TERMINAL=console[/FONT]  didn't help at all: the grub menu was in 80*24 mode, but at some point  while booting, the kernel activated the framebuffer (output was well  aligned). However, when the system was up and ready, switching to the  console, I found myself back in 80*24 mode, but there was no login  prompt. Instead, I saw just some log output, identical on all consoles.

Any suggestions?

---

