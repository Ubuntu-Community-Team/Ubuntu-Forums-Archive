---
title: "Boot Issues After Power Cut"
date: 2024-03-26
forum: General Help
---

### Post by refresherm on 2024-03-26
Hi all,

Had a power cut the other day whilst my PC was on, and now it won't boot. I've tried removing ```
quiet splash
``` from the kernel parameters to see where it goes wrong, and it hangs at:

```
Started realtimekit scheduling policy service
```

I've tried running fsck -f from a Live CD, but it doesn't seem to find any errors. I've also tried running boot-repair, but it still gets stuck at the same place. Here's the boot-repair log if it helps: [https://pastebin.ubuntu.com/p/jZ6FrBX3fS/](https://pastebin.ubuntu.com/p/jZ6FrBX3fS/).

Not really sure what else to try. Thanks in advance for any ideas!

---

### Post by refresherm on 2024-03-26
Just wanted to update that I've fixed this. I removed all of my Nvidia drivers (in recovery mode), which allowed me to boot. I could then re-install the graphics drivers. I also had to remove /etc/X11/xorg.conf. Everything would then boot normally.

---

### Post by ajgreeny on 2024-03-26
Welcome to the forum and thanks for letting everyone know!

Please now use the Thread Tools up top to mark this thread as SOLVED.
It is a great help to others searching the forum.

---

