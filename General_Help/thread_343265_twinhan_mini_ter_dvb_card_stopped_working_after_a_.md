---
title: "twinhan mini ter dvb card stopped working after a reboot"
date: 2007-01-21
forum: General Help
---

### Post by michael48 on 2007-01-21
Hello,

After months of running updates without rebooting, my dvb card stopped working after I finally rebooted. In dmesg, I get
(sorry if the paste looks bad)

```

[775506.724243] bttv: driver version 0.9.16 loaded
[775506.724251] bttv: using 8 buffers with 2080k (520 pages) each for capture
[775506.724731] bttv: Bt8xx card found (0).
[775506.724885] bttv0: Bt878 (rev 17) at 0000:02:03.0, irq: 19, latency: 64, mmio: 0xf8001000
[775506.725161] bttv0: subsystem: feff:0001 (UNKNOWN)
[775506.725167] please mail id, board name and the correct card= insmod option to video4linux-list@redhat.com
[775506.725174] bttv0: using: Twinhan DST + clones [card=113,insmod option]
[775506.726331] bttv0: gpio: en=00000000, out=00000000 in=00f500ff [init]
[775506.726648] bttv0: using tuner=4
[775506.746654] bttv0: add subdevice "dvb0"
[775506.761664] bt878: AUDIO driver version 0.0.0 loaded
[775506.761894] bt878: Bt878 AUDIO function found (0).
[775506.761907] ACPI: PCI Interrupt 0000:02:03.1[A] -> GSI 19 (level, low) -> IRQ 19
[775506.761915] bt878_probe: card id=[0x1feff], Unknown card.
[775506.761916] Exiting..[775506.761921] ACPI: PCI interrupt for device 0000:02:03.1 disabled
[775506.762717] bt878: probe of 0000:02:03.1 failed with error -22
[775506.779051] dvb_bt8xx: unable to determine DMA core of card 0,
[775506.779058] dvb_bt8xx: if you have the ALSA bt87x audio driver installed, try removing it.
[775506.779509] dvb-bt8xx: probe of dvb0 failed with error -14

```

I'm pretty sure it's card 113, although I can't find the box it came in.

I've check if the alsa modules is loaded, it isn't. I blacklisted it just in case.


lspci looks like

```

02:03.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:03.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)

```

any ideas?

---

### Post by bondjames_12 on 2007-03-25
My Twinhan card is also having this problem. I crashed X and restarted using the reset button and it came back up and mythtv wouldn't work. After investigating I found mine to have the exact issue as yours. Exactly. and yep Twinhan cards are 113.

I'll post here if I figure anything out.

---

### Post by bondjames_12 on 2007-03-25
Solved my problem. I remembered I set the Plug and Play to YES in my bios, so I set it back to no and the IRQ problem went away.

---

