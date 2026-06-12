---
title: "Debug log: &quot;Mode Sense: 00 3a 00 00&quot; any ideas?"
date: 2007-05-30
forum: General Help
---

### Post by willmcgregor on 2007-05-30
Hi all,



Im having a problem with my ubuntu box restarting randomly the only thing i can find in the logs around the time the reasts happen is this: "Mode Sense: 00 3a 00 00"

Excerpt from /var/log/debug:
```

...
May 29 21:38:25 bubbles kernel: [119427.039250] sde: Mode Sense: 00 3a 00 00
May 29 21:39:08 bubbles kernel: [119469.417674] sde: Mode Sense: 00 3a 00 00
May 29 21:40:17 bubbles kernel: [119538.528065] sde: Mode Sense: 00 3a 00 00
May 29 21:40:29 bubbles kernel: [119550.128561] sde: Mode Sense: 00 3a 00 00
May 29 21:40:30 bubbles kernel: [119551.983467] sde: Mode Sense: 00 3a 00 00
May 29 21:40:34 bubbles kernel: [119555.662171] sde: Mode Sense: 00 3a 00 00
May 29 21:40:41 bubbles kernel: [119562.658709] sde: Mode Sense: 00 3a 00 00
May 29 21:41:03 bubbles kernel: [119585.032360] sde: Mode Sense: 00 3a 00 00
May 29 21:41:05 bubbles kernel: [119586.625347] sde: Mode Sense: 00 3a 00 00
May 29 21:41:08 bubbles kernel: [119589.472387] sde: Mode Sense: 00 3a 00 00
May 29 22:33:52 bubbles kernel: [122750.942940] sde: Mode Sense: 00 3a 00 00
...

```

Im running:

Ubuntu 7.04 (the names confuse me:confused:)

Then after doing that for a while the PC restarts. Does anyone know what this means and if it could be related to the restarts?


Thanks in advance,

Will.

---

