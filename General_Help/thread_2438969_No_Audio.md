---
title: "No Audio"
date: 2020-03-20
forum: General Help
---

### Post by box02-0 on 2020-03-20
Hi.

I have no Audio on my Dell 7791 laptop which is using a Realtek ALC3271 Audio Device Driver running Ubuntu 18.04. (The UEFI/BIOS tells me it is a Realtek ALC3271.)  When I boot with Windows 10, the Audio is fine.

In System Settings - Sound – it shows “Dummy Output”, and no Sound Cards are detected.

I have tried killing pulseaudio and rebooting, and 

sudo alsa force-reload
boot

and 

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
boot

to no avail.

The output is NOT muted.

I’ve even tried shutting Audio off through the UEFI/BIOS, booting, and turning Audio back on.

I went into Synaptic and downloaded anything to do with Alsa and booted. ZIP!

In Terminal:

lspci -nn | grep -i audio
00:1f.3 Multimedia audio controller [0401]: Intel Corporation Device [8086:02c8]

which is the only indication that Ubuntu is seeing some sort of Audio controller.

I’ve played with this yesterday and today and I’ve run out of steam. 

Any suggestions would be greatly appreciated.

Thanks,
M...

---

### Post by TheFu on 2020-03-20
Most Ubuntu versions use pulse audio.
There is a sound troubleshooter that google finds.  It will generate lots of output for the sound gurus to look over.

---

