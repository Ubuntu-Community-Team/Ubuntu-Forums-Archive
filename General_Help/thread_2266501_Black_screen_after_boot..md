---
title: "Black screen after boot."
date: 2015-02-23
forum: General Help
---

### Post by Tom_Hoff on 2015-02-23
Hey guys I need some help if anyone has any ideas. My laptop recently got a black screen after boot, then nothing. This seems to be a graphical error because If I do ctrl + alt + f1, I can access the consol there. 

I'm trying to fix this by re-installing the system via LiveCD (the system re-install, not complete wipe so I keep my files), but the re-install option on the liveCD isn't there. Does anyone know whats up?

---

### Post by Ruben_van_Smirren on 2015-02-24
reinstall the server on another partition, then recover the data via the fresh install!

---

### Post by Bashing-om on 2015-02-24
Tom_Hoff; Hello;

Yeah, could well be a graphics issue.
What results when booting with the 'nomodeset' boot parameter ( change the driver later) ?
@ grub boot menu 'e' key for edit mode. add 'nomodeset' after "quiet splash", ctl +x to continue the boot process.

[INDENT][INDENT]maybe YES
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Tom_Hoff on 2015-03-03
Hi, thanks for your responses.

Ruben, I want to avoid that if possible.

Bashing-om I did that, seemed to make everything go back to default resolution, but nothing, still black screen. Any ideas?

Tom

---

### Post by Tom_Hoff on 2015-03-03
Haha :P a forum full of ubuntu users, no one has had this before? :O

---

### Post by Bashing-om on 2015-03-03
Tom_Hoff; Humm ...

> **Tom_Hoff said:**
> Haha :P a forum full of ubuntu users, no one has had this before? :O

Not much to go on yet .
Are you running a proprietary graphics driver; such that it got broke in a update process ?
What video card are we working with ?
```

lspci -vnn | grep VGA -A 12

```

Maybe power management ?
What results booting with say the "acpi=off" boot parameter, or some others ?

Nothing last forever, has the video card died ?
What results when booting a liveDVD ?

[INDENT][INDENT]trials troubles and tribulations
[INDENT][INDENT][INDENT]find the cause, find the solution
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Colo2 on 2015-03-03
Thanks for your reply ;) i'll give these things a try tomorrow.

---

