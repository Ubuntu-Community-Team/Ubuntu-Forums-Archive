---
title: "Modules"
date: 2007-09-09
forum: General Help
---

### Post by arm-c on 2007-09-09
OK.  I am using Xubuntu.  I am trying to get the sound to work on my computer, but I can't --- so far.  I have tried modprobe but it returns errors that it can't find the modules, however, I can find those modules on my computer.  The problem is that it looks in the /lib/kernel/2.6.xxx-generic instead of the /lib/kernel/2.6.xxx-i386 location for the files.

How do I make it see the other location???

---

### Post by 5-HT on 2007-09-09
Modules are compiled for a specific kernel version: You'll need to boot into the other(386) kernel to use the 386 modules- there's no mixing and matching.
However, the same modules (give or take) should be available for both kernels...especially for sound cards. Which module are you trying to load and what's the exact error?

cheers,

---

### Post by arm-c on 2007-09-09
1st question, is how do I boot into the other kernel... I only am running the 2.6.20.15 kernel or something like that (I know there is a 16 out now).  Xubuntu didn't give me the option to "upgrade" to the new kernel... and besides, I am trying to get the basics working.

Specifically, the modules I am trying to load are the sound core and drivers for my sound card on that old laptop.  I am not at it now, or I would pull up the exact errors.  The sound card is an ISA card CS4237b that is not automatically detected, although I can see in the sound card and it is listed as active in the /sys/devices/pnp0 sub directory where the resources are (I don't think the exact folder matters).

When I run 'modprobe' it returns errors that 6 or 7 files are unable to be found.  In every instance, it is looking for the module in:

     /lib/modules/2.6.20-15-generic/kernel/sound/isa

I did a find and located the files in the following location:

    /lib/modules/2.6.20-15-i386/kernel/sound/isa

A look in the generic location showed the directories to be empty.  Is there a way to get them back in the 'generic' side??

What I have tried already:

   Downloading and compiling the drivers for the sound card from ALSA site.  Each time it returns an error to me and apparently aborts the compile process.

   Tried 'reinstalling' the alsa-utils, alsa base, and linux-sound packages through symantic.  Didn't fix anything.

    Posting here for information on what to do.... :)

Here are the exact errors from "modprobe":

modprobe snd-cs4236 isapnp=0 port=0x530 cport=0x210 irq=5 dma1=1 dma2=0
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-page-alloc.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-timer.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-pcm.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4231-lib.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/seq/snd-seq-device.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-rawmidi.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4236-lib.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/core/snd-hwdep.ko': No such file or directory
WARNING: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/drivers/opl3/snd-opl3-lib.ko': No such file or directory
FATAL: Could not open '/lib/modules/2.6.20-15-generic/kernel/sound/isa/cs423x/snd-cs4236.ko': No such file or directory

---

