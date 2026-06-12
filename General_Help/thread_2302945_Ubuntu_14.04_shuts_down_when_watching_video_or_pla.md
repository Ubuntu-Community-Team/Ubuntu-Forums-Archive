---
title: "Ubuntu 14.04 shuts down when watching video or playing games"
date: 2015-11-14
forum: General Help
---

### Post by b77d77 on 2015-11-14
I've run into a problem recently where Ubuntu will shutdown after 10-30 minutes of watching a youtube video or playing minecraft. I've checked with lm-sensors and the temperature doesn't go above 50°C when watching video, or about 55-60°C playing minecraft, but it still shuts down. When it shuts down it's not an instant shut off, programs will close and the ubuntu logo comes up and it shuts down. I'm using a laptop with an integrated Intel processor/graphics (I'm not good with hardware). I also have windows installed and it still plays video and games with no problem. Any ideas what to do?

---

### Post by tgalati4 on 2015-11-15
Welcome to the forums.

Remove the battery and boot with the AC cord only.  A bad battery can cause power issues (like low voltage) which will trigger a BIOS shutdown.  Windows probably uses less power (I bet you get longer battery life), so you don't see the issue.

---

### Post by b77d77 on 2015-11-15
> **tgalati4 said:**
> Welcome to the forums.

Remove the battery and boot with the AC cord only. A bad battery can cause power issues (like low voltage) which will trigger a BIOS shutdown. Windows probably uses less power (I bet you get longer battery life), so you don't see the issue.

I tried without the battery, still having the same problem.

---

### Post by tgalati4 on 2015-11-16
It's possible that the power brick is worn out, or your heat sink for the CPU and GPU (they are often shared) is clogged with dust.  Since it appears to be a controlled shutdown, look through the log files for clues.

Open a terminal:

```
more /var/log/syslog
```

---

