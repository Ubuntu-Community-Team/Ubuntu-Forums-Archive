---
title: "Sound Dummy Output"
date: 2019-11-27
forum: General Help
---

### Post by favazi on 2019-11-27
I am using Ubuntu 16.04 (kernel 4.4.0-150-generic). I have lost sound after I installed an NVIDIA RTX GPU card. I have tried all of the solutions in top google searches, but none of them worked.

Here is what I get:
> 
$ sudo alsa force-reload
Unloading ALSA sound driver modules: (none loaded).
Loading ALSA sound driver modules: (none to reload).



and

> 
$ lspci -nnk | grep -A2 Audio
00:1b.0 Audio device [0403]: Intel Corporation C610/X99 series chipset HD Audio Controller [8086:8d20] (rev 05)
    Subsystem: Dell C610/X99 series chipset HD Audio Controller [1028:0619]
00:1c.0 PCI bridge [0604]: Intel Corporation C610/X99 series chipset PCI Express Root Port #1 [8086:8d10] (rev d5)
    Kernel driver in use: pcieport
--
08:00.1 Audio device [0403]: NVIDIA Corporation Device [10de:10f7] (rev a1)
    Subsystem: NVIDIA Corporation Device [10de:12a3]
08:00.2 USB controller [0c03]: NVIDIA Corporation Device [10de:1ad6] (rev a1)


and

> 
$ pulseaudio 
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.


The sound settings show "Dummy Output". I appreciate it if anybody can help with this.

---

