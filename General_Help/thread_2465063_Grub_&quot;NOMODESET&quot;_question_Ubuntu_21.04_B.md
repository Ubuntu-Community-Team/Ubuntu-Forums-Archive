---
title: "Grub &quot;NOMODESET&quot; question Ubuntu 21.04 Blinking Monitor on start"
date: 2021-07-20
forum: General Help
---

### Post by estamets on 2021-07-20
Good Morning Good Afternoon or Good Night all,

I'm running into an intermittent problem. Occasionally, I start my system and I get the POST screen and then it just goes blank after that. I have to cold power off and restart the process.. After that, it seems to work again. It's sort of a crap shoot when it does it.

The fix, I have discovered, is to edit grub to "NOMODESET". This does in fact work. I do find the results a bit unsatisfactory however. I have discovered that when that switch is made, it defaults to X11 instead of Wayland.

I have grown to like Wayland. It just seems like a smoother experience and playing videos on youtube and such uses a few fewer CPU cycles than in X11. Is there a way to consistently get this fixed without the undesired NOMODESET fix? Something my Google-Fu hasn't come up with?

Here's my graphics card info if it's relevant. More details can be provided if needed.

*-display
                description: VGA compatible controller
                product: Oland [Radeon HD 8570 / R5 430 OEM / R7 240/340 / Radeon 520 OEM]
                vendor: Advanced Micro Devices, Inc. [AMD/ATI]
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 87
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=0
                resources: irq:129 memory:a0000000-afffffff memory:b1100000-b113ffff ioport:3000(size=256) m

---

### Post by CatKiller on 2021-07-20
nomodeset is a nuclear option; it's not a good choice for running permanently.

It seems feasible that the times you're panicking about the blank screen, the system's just doing an automatic fsck, and the text mode resolution isn't supported by your monitor. What happens if you just leave it?

---

