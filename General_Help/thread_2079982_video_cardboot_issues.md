---
title: "video card/boot issues"
date: 2012-11-02
forum: General Help
---

### Post by jcpahman77 on 2012-11-02
System is a 64 AMD Athlon Dual Core and an ATI 5770 PCIe video card.

I finally got the video card to work, forgot to switch it to the default video card in the bios ](*,)

When I did that though I lost all other sound devices in the sound control panel (video card has HDMI) and the mobo has 7 channel analog audio along with a coax digital output. I thought I'd try switching back to the onboard graphics as the default graphics card in the bios but when I do that it dumps me to a terminal window on boot-up. I don't *need* the onboard audio as this is primarily going to be a HTPC but it would be nice to have for times I want to use it not connected to my AVR. I'm new to Ubuntu but I'm picking it up quickly. I'm no stranger to a command line interface, I grew up with computers from DOS 3.3 on, but I don't know the linux commands well enough yet to go looking for the solution on my own.

Can someone point me in the right direction? I'm very impressed with 12.04 so far and am looking forward to using it more in the future.

---

### Post by jcpahman77 on 2012-11-02
Dang it, more bios fail. There is an option for the onboard audio with options of "auto" "enable" or "disable". I had it set to "auto", switching it to "enable" fixed the problem of the sound. I'm going to keep working on the boot problem, but I think I've got things configured just about perfect for my use right now.

---

