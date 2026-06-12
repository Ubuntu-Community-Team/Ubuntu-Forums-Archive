---
title: "Screen tearing only in specific monitor config"
date: 2012-10-31
forum: General Help
---

### Post by misterhektik on 2012-10-31
Some basic info:

Ubuntu 12.10
Nvidia 570 GTX using nvidia-current-updates package
Unity
Main Mointor: 1920x1200 landscape connected via DVI
Second Monitor: 1080x1200 portrait connected via VGA

I am getting terrible screen tearing on my main monitor only when my main monitor is in landscape mode, and my second monitor is in portrait mode. However, on the other configurations I've tried (main/second: landscape/landscape, portrait/portrait, portrait/landscape), there is no tearing/vsync issues on either monitor. The issue only shows up when in landscape/portrait and only on the main monitor.

Some things I've tried that haven't worked include: 
compiz config "sync to vblank" on/off
compiz config "don't wait for vsync" on/off
compiz conifg "force synchronization between x and glx" on/off
nvidia settings "sync to vblank" on/off
nvidia settings "sync to this display device" main/second

I appreciate anyone who can shed some light on this problem. If you need more info, let me know.

---

