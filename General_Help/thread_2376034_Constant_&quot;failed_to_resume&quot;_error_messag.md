---
title: "Constant &quot;failed to resume&quot; error messages"
date: 2017-10-29
forum: General Help
---

### Post by qaz8 on 2017-10-29
I'm currently running Ubuntu 16.04 LTS, and every time I resume after suspending, two error messages show up on a black screen:

```

dpm_run_callback(): usb_dev_resume+0x0/0x20 returns -32
PM: Device 1-7 failed to resume async: error -32

```

It goes away after a few seconds and then Ubuntu resumes normally, and everything seems to work fine. But after about 5 resumes it stays on the screen with the error messages, and the only way to get out of it is to hold the power button to turn of the computer. There's some more info in the logs:

```

[11402.990670] usb 1-7: reset full-speed USB device number 3 using xhci_hcd
[11403.090762] [drm] RC6 on
[11403.120234] usb 1-7: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[11403.121112] dpm_run_callback(): usb_dev_resume+0x0/0x20 returns -32
[11403.121124] PM: Device 1-7 failed to resume async: error -32

```

The only USB device I have plugged in is a USB mouse, which works normally after resuming. I've tried unplugging the mouse before suspending and plugging it in after resuming, but the same error messages show up. I have no idea what's going wrong.

---

