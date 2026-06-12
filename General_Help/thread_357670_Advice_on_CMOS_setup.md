---
title: "Advice on CMOS setup"
date: 2007-02-09
forum: General Help
---

### Post by ricardisimo on 2007-02-09
When I go into CMOS at boot, there are a few options in "Advanced Setup" that I'm curious about, primarily "Graphic Win Size" which is currently set at 64MB, but with lower (32MB) and higher (128MB) options available. Normally in the compootor world, it's the superlatives and diminutives that are the "best" options, so I'm a bit sceptical whenever I see  a Three Little Bears "just right" option.

I'd also like to know how much I can or should play around with the following:
[LIST]
[*]DRAM Voltage [currently set to 2.5V]
[*]Spread Spectrum [currently disabled]
[*]Hyper-Threading Function [currently disabled]
[*]Performance Mode Select [currently disabled]
[*]DRAM CAS# Latency [currently "By SPD"]
[/LIST]
Thanks in advance.

---

### Post by ~LoKe on 2007-02-09
Are you overclocking?  If not, **touch nothing**.

The BIOS is an overclockers too, excluding IDE configurations.

---

### Post by old_geekster on 2007-02-09
First, not to belittle you, simply to correct a misconception, the settings that you are discussing are in the BIOS (Basic Input Output System).  The CMOS is where the settings in the BIOS are saved.

Now, to answer your questions:

1.  Graphic Win Size:  This BIOS feature does two things. It selects the size of the AGP aperture (hence, the name Graphic Windows Size) and it determines the size of the GART (Graphics Address Relocation Table).

The aperture is a portion of the PCI memory address range that is dedicated for use as AGP memory address space while the GART is a translation table that translates AGP memory addresses into actual memory addresses which are often fragmented. The GART allows the graphics card to see the memory region available to it as a contiguous piece of memory range.

2. * DRAM Voltage [currently set to 2.5V] Voltage to your RAM.  Probably at max.
    * Spread Spectrum [currently disabled] To do with Hard drives.  
    * Hyper-Threading Function [currently disabled] Function of your CPU.
    * Performance Mode Select [currently disabled] (Not sure about this one.)
    * DRAM CAS# Latency [currently "By SPD"] Column Address Strobe (First number in RAM timings: (3 - CAS),4,4,8.  The SPD is the default timings of the RAM for the system to read.  It is encoded in the RAM by the manufacturer.

As an Overclocker, my advice is don't mess with any of them until you do much research.  You can do more harm than good, especially with the DRAM voltage.

Hope this helps.

---

### Post by ricardisimo on 2007-02-09
So you're both telling me to ***_do nothing_***. I happen to be exceptionally good at just that, as my wife can attest.

"CMOS Setup" is what that particular screen is actually called. Until I spoke with you two I had no conception at all, and therefore certainly not a misconception. ;-)

I thank you both mightily.

---

### Post by ~LoKe on 2007-02-10
Basically what the overclocking features in a BIOS do are voltage and speed increases.

By raising your vCore, you're increasing the amount of power you're sending to your processor.  More power = more heat = shorter lifespan.  If you raise the vCore too high, you risk frying your processor sooner than desired (as if it's desired at all?).

Same basically goes for vDimm.  That's the voltage for your ram, and can cause the same problems.  It can also cause the dreaded BSOD in Windows.  Not sure of it's effects in Linux, but I imagine it would be similar to a hard lockup.

Changing the FSB (Front side Bus) is relatively safe to do.  You can push it as high as you'd like, because if you go too high, your computer just won't boot.  If that's the case, your BIOS might notice and temporarily set your settings to stock so you can boot into the BIOS and fix it.  Worst case scenario, you end up clearing your CMOS (easy) and you're back up, no damage.

RAM timings are tricky little buggers.  If you're having lockups and BSOD's while overclocking your processor, it might be because your memory timings are too tight.  The higher the number, the looser the timings.  Looser timings are more "forgiving" in terms of overclocking.  The goal of an overclocker is to get the lowest timings and the lowest voltages possible, and still maintain a stable system.

---

### Post by old_geekster on 2007-02-10
> **ricardisimo said:**
> So you're both telling me to ***_do nothing_***. I happen to be exceptionally good at just that, as my wife can attest.

"CMOS Setup" is what that particular screen is actually called. Until I spoke with you two I had no conception at all, and therefore certainly not a misconception. ;-)

I thank you both mightily.
Well, I tell ya, you have a great sense of humor.  Nobody can take that away from you.

I didn't understand all of those settings a year ago.  But since then, I became extremely interested in Overclocking for gaming.  Along with that came the necessity to learn as much about the BIOS and RAM timings as I could.  DFI boards have some of, if not the best, BIOS settings in the industry.  They specialize in computer enthusiast components.

At 61 years old, I will never learn any younger.  So, now I am into learning Linux/Ubuntu.

---

### Post by dcstar on 2007-02-10
> **ricardisimo said:**
> When I go into CMOS at boot, there are a few options in "Advanced Setup" that I'm curious about, primarily "Graphic Win Size" which is currently set at 64MB, but with lower (32MB) and higher (128MB) options available. Normally in the compootor world, it's the superlatives and diminutives that are the "best" options, so I'm a bit sceptical whenever I see  a Three Little Bears "just right" option.

I'd also like to know how much I can or should play around with the following:
[LIST]
[*]DRAM Voltage [currently set to 2.5V]
**[*]Spread Spectrum [currently disabled]**
**[*]Hyper-Threading Function [currently disabled]**
**[*]Performance Mode Select [currently disabled]**
[*]DRAM CAS# Latency [currently "By SPD"]
[/LIST]
Thanks in advance.

**Spread spectrum** gives your master clock a "wobble" so your PC isn't generating potential interference on one locked set of frequencies (it spreads any interference around to more frequencies - but the energy is less on any particular frequency) - it doesn't really affect performance too much.

If you have a **Hyper-threading** capable CPU you can enable this option, and then install a SMP kernel that may well provide better performance. Give it a try.

The **Performance Mode** may set your motherboard into a more aggressive group of settings that could potentially improve performance - another thing worth trying but beware that usually this comes at the price of reliability.

---

### Post by ~LoKe on 2007-02-10
Most of the advanced enabled/disabled settings are turned off when overclocking.  This relieves stress that may be put on the CPU to achieve the highest overclock possible.  Again, if you don't o/c, it's probably best to leave them where they're at, or at the most, turn them on.

---

