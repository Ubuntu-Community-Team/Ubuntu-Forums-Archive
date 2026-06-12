---
title: "Xubuntu"
date: 2007-03-10
forum: General Help
---

### Post by Harriscat on 2007-03-10
I have decided to use the Xubuntu distro as normal ubuntu does not seem to have any compatibility with my laptops graphics card, I have a compaq with an nvidia graphics card and a AMD Turion™ 64 X2 Mobile processor, Which version of xubuntu should i download?


thanks

charlie

---

### Post by yabbadabbadont on 2007-03-10
The version of xorg used by both is the same...  it is only the default desktop and package selection that is different.  If regular Ubuntu doesn't work, the same version of Xubuntu and Kubuntu won't either.  Which version did you try?  (Dapper, Edgy, Feisty)

---

### Post by Harriscat on 2007-03-10
I used Edgy and i am having terrible problems with it

---

### Post by llamakc on 2007-03-10
Which NVidia graphics card does it have? 

You can run:

```


sudo lshw

```(and look for the bit about your card) and paste that here [if you don't know which one you have]

Mine (ATI) looks like this:

```

*-display:0
             description: VGA compatible controller
             product: RV370 5B60 [Radeon X300 (PCIE)]
             vendor: ATI Technologies Inc
             physical id: 0
             bus info: pci@05:00.0
             logical name: /dev/fb0
             version: 00
             size: 128MB
             width: 32 bits
             clock: 33MHz
             capabilities: vga bus_master cap_list fb
             configuration: depth=16 frequency=75.69Hz mode=1024x768 visual=truecolor xres=1024 yres=768
             resources: iomemory:d8000000-dfffffff ioport:9e00-9eff iomemory:fe2f0000-fe2fffff irq:58
        *-display:1 UNCLAIMED
             description: Display controller
             product: RV370 [Radeon X300SE]
             vendor: ATI Technologies Inc
             physical id: 0.1
             bus info: pci@05:00.1
             version: 00
             size: 64KB
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:fe2e0000-fe2effff

```And with the command `lspci -v` I see this:

```

05:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] (prog-if 00 [VGA])
        Subsystem: ATI Technologies Inc Unknown device 1b60
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at d8000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 9e00 [size=256]
        Memory at fe2f0000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at fe200000 [disabled] [size=128K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0
        Capabilities: [80] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [100] Advanced Error Reporting

05:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
        Subsystem: ATI Technologies Inc Unknown device 1b61
        Flags: fast devsel
        Memory at fe2e0000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Express Endpoint IRQ 0

```Giving folks that info will help solve your problem (hopefully).

---

### Post by jem7v on 2007-03-10
As yabbadabbadont said, each version of Ubuntu uses the same version of Xorg, but more significantly, they all use the same video card drivers too.  Are you having trouble with the default **nv** driver, or with the proprietary **nvidia** driver?

---

### Post by Harriscat on 2007-03-10
I have made about 2 posts about this and no one will help
I boot up ubuntu it goes to the loading screen when it loads it goes to a blank screen
when i try to do the non gaphical login it starts the non graphical login but then it just disapears?

CAN ANYBODY HELP ME?


thanks

charlie

---

### Post by jem7v on 2007-03-10
One thing you might try is switching to a different terminal - I think there are seven of them. To do that you use Ctrl+Alt+F(1-7)... The terminal that contains your desktop manager should be F7, and the other 6 are there to use for times such as these when things go stupid. You should probably be able to log into one of them and work with your system from the command line that way.  If not, I'm really not sure what's wrong.

P.S. I read your other posts, and you still haven't told us what NVidia card you're using (I know it's a laptop, but it should still have a model) or which driver you're using (nv or nvidia).  It would probably help us diagnose the problem if we knew exactly what hardware you are using.

---

### Post by Harriscat on 2007-03-10
I think iim just going to go back to windows i just cant be arsed with all this ****

thanks

charlie

If i was able to help myself at all i would have done but ubuntu has turned my laptop into a potato

thanks again

charlie

---

### Post by strabes on 2007-03-10
Sorry to hear that. Linux sometimes takes some effort to get working correctly but once it is up and running, it's worth it.

---

