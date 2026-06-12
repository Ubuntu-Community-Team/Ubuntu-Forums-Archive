---
title: "SMART TV Not Connecting"
date: 2021-10-06
forum: General Help
---

### Post by heinrichklopper on 2021-10-06
Hi. I am using Ubuntu 20.04, trying to connect it to a SMART Brand TV via HDMI. It does not work - the screen doesn't even show up in settings. Connecting works on Windows.

---

### Post by TheFu on 2021-10-06
Verify that the output from the computer matches one of the approved inputs to the TV.  We're talking resolution and refresh rates.
I'd start with 1280x720 at 60Hz, then move up in resolution.

If using X/Windows, the settings can be controlled using xrandr or a GUI tool like lxrandr or arandr.  I have no idea how to do the same with Wayland. Sorry.

---

### Post by heinrichklopper on 2021-10-13
Hi. Sorry for replying so late. Somehow it worked when I first connected the screen to a Windows machine and then the Ubuntu computer. I can only theororise why that worked, but the bottom line is that it did. Thanks for responding, have a great day.

---

### Post by heinrichklopper on 2021-10-13
Okay so update. It was because I had 'nomodeset' in my /etc/default/grub file. No clue what it does, but I know it does bad things.

---

### Post by TheFu on 2021-10-13
If this is solved, please use the Thread Tools button to help the community out.

nomodeset isn't meant to be used beyond very specialized situations. Some GPUs need it used before the proprietary driver gets installed or if the GPU is so old that a proprietary driver isn't supported any longer.

---

