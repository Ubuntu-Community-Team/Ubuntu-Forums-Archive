---
title: "Display manager crashes in suspend, 6.8.0-47 (not 6.8.0.45)"
date: 2024-10-27
forum: General Help
---

### Post by YesWeCan on 2024-10-27
Just noticed that in the latest kernel update, my Ubuntu 24.04 LTS display won't come out of suspend. Fans come on, etc., but screen remains blank. I can log in remotely by CLI and I can recover by restarting the display manager. This does not happen in 6.8.0.45.
Just wondering if anyone else has observed this?
Brian

Edit. It seems to work ok with 6.8.0-47 when I set the "screen blank" power setting to "never". Is there a problem with the screen blanker not responding to keyboard and mouse inputs after a suspend? Odd, since a key press will un-suspend the OS.

---

