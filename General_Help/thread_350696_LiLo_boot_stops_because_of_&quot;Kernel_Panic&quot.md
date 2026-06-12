---
title: "LiLo boot stops because of &quot;Kernel Panic&quot;"
date: 2007-01-31
forum: General Help
---

### Post by Cariboo1938 on 2007-01-31
I have a dual boot system with OSs on two separate hard drives (sda: Ububtu, sdb: Windows) and often I use the GAG47 boot floppy to select the OS I want to use. This worked fine until recently.

I don't know if this makes any sense, but after installing and uninstalling "FrostWire" with Automatix I'm expriencing a boot problem using my GAG47 boot floppy, which uses LiLo to select the OS.
The Boot procedure stops with this messages:

[ 34.257843] drivers/rtc/hctosys.c: unable to open rtc device(rtc0)
[ 34.326749] VFS: Cannot open root device"802" or unknown-block(8,2)
[ 34.326801] Please append a correct "root=" boot option
[ 34.326851] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,2)

This is reproducible and I have to make a hardware reset and boot in GRUB.
I wonder what I would have to do with this message 'append a correct "root=" boot option?
Any thoughts or ideas?

---

### Post by Cariboo1938 on 2007-01-31
](*,)Bummmmppppp!!!

---

### Post by Cariboo1938 on 2007-02-02
I really have no clue what happened that I couldn't boot with GAG boot floppy anymore.
I re-installed LiLo and now it works again. 
Case put to rest !

---

