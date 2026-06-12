---
title: "Memory Slots"
date: 2020-08-09
forum: General Help
---

### Post by Geoff_Lane on 2020-08-09
Folks,

Have a Toshiba Satellite laptop, initially 4GB ram but upgraded with 8GB to 12 total.

Viewing the output of lshw I see the original memory is clock 1600MHz and is in bank0 and the newer memory is faster at clock 1866MHz in bank1

Computer seems to be functioning OK but free -h gives me the following;
```
free -h

              total        used        free      shared  buff/cache   available
Mem:            10G        1.7G        6.3G         60M        2.7G        8.7G
Swap:          2.0G          0B        2.0G

```

So, does it matter which slot I have the two memory modules in and any idea why free -h shows 10G total whereas it is 12G?

Geoff

---

### Post by ActionParsnip on 2020-08-09
Yes, 10Gb RAM so your system is probably using 2Gb for video RAM.
You are currently using 1.7Gb RAM to run the OS (When the command was ran).
You have 2Gb of swap space.

What's the issue?

---

### Post by Geoff_Lane on 2020-08-25
> **ActionParsnip said:**
> Yes, 10Gb RAM so your system is probably using 2Gb for video RAM.
You are currently using 1.7Gb RAM to run the OS (When the command was ran).
You have 2Gb of swap space.

What's the issue?

My post never indicated there was an issue.

I merely asked if, as each RAM appears to run at a different speed, whether it mattered which slot the individual memory modules were inserted in to.

Geoff

---

### Post by ActionParsnip on 2020-08-25
Do you use integrated video hardware or do you have a separate video card? If you use integrated then the system RAM will be used as video RAM

---

### Post by Yellow Pasque on 2020-08-25
> **Geoff_Lane said:**
> I merely asked if, as each RAM appears to run at a different speed, whether it mattered which slot the individual memory modules were inserted in to.

They may be rated at different speeds, but they won't run at different speeds. The BIOS/EFI will select the slower speed so as not to overclock the slower stick.
For example, if you have a stick of DDR3-1660 and DDR3-1866, the system will run them at DDR3-1600 speed.

---

### Post by Yellow Pasque on 2020-08-25
Ah, I get it. You probably looked at the wrong part of lshw output. The important part is the clock field. That is the actual speed it is currently running at, rather than the speed it is capable of.

```
*-bank:1
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
          product: CL16-18-18 D4-3200
          vendor: Unknown
          physical id: 1
          serial: 00000000
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
=====>         clock: 3200MHz (0.3ns)      <======
```

---

### Post by Geoff_Lane on 2020-09-15
> **Yellow Pasque said:**
> Ah, I get it. You probably looked at the wrong part of lshw output. The important part is the clock field. That is the actual speed it is currently running at, rather than the speed it is capable of.

```
*-bank:1
          description: DIMM DDR4 Synchronous Unbuffered (Unregistered) 3200 MHz (0.3 ns)
          product: CL16-18-18 D4-3200
          vendor: Unknown
          physical id: 1
          serial: 00000000
          slot: DIMM 1
          size: 8GiB
          width: 64 bits
=====>         clock: 3200MHz (0.3ns)      <======
```

The clock field was the field I looked at and were the figures quoted in my original post as shown below;

> *-bank:0
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1600 MHz (0.6 ns)
             product: M471B5173DB0-YK0
             vendor: Samsung
             physical id: 0
             serial: 13886699
             slot: DIMM 0
             size: 4GiB
             width: 64 bits
             clock: 1600MHz (0.6ns)
        *-bank:1
             description: SODIMM DDR3 Synchronous Unbuffered (Unregistered) 1866 MHz (0.5 ns)
             product: 16KTF1G64HZ-1G9P1
             vendor: Micron Technology
             physical id: 1
             serial: 1FDA888E
             slot: DIMM 1
             size: 8GiB
             width: 64 bits
             clock: 1866MHz (0.5ns)

All I asked was as both modules are rated at different speeds does it matter which bank they are in?

Geoff

---

### Post by Autodave on 2020-09-15
Normally, no it doesn't.  I have always preferred to have the slowest in the the first slot, but that really goes back quite a few years to when it did make a difference.  Older computers were fussy about things like that.

---

### Post by Geoff_Lane on 2020-10-30
> **ActionParsnip said:**
> Do you use integrated video hardware or do you have a separate video card? If you use integrated then the system RAM will be used as video RAM

Wasn't aware a laptop could have a separate video card.  It is whatever is on the motherboard.

geoff

---

### Post by Geoff_Lane on 2020-10-30
Geoff

---

### Post by Geoff_Lane on 2020-10-30
> **Yellow Pasque said:**
> They may be rated at different speeds, but they won't run at different speeds. The BIOS/EFI will select the slower speed so as not to overclock the slower stick.
For example, if you have a stick of DDR3-1660 and DDR3-1866, the system will run them at DDR3-1600 speed.

That makes sense.

Geoff

---

### Post by CelticWarrior on 2020-10-30
> [COLOR=#000000]Wasn't aware a laptop could have a separate video card.[/COLOR]

They can and they do.
iGPUs nowadays aren't in the motherboard itself but in the CPU, pretty much like all modern ARM chips always did.
So, entry and medium level laptops typically have just a iGPU, Intel or AMD. Gaming laptops typically have an additional and switchable dGPU (discrete GPU), Nvidia or AMD. This dGPU typically but not always is mounted in a separated board that may or may not be replaced.

---

### Post by Geoff_Lane on 2020-11-01
> **CelticWarrior said:**
> They can and they do.
iGPUs nowadays aren't in the motherboard itself but in the CPU, pretty much like all modern ARM chips always did.
So, entry and medium level laptops typically have just a iGPU, Intel or AMD. Gaming laptops typically have an additional and switchable dGPU (discrete GPU), Nvidia or AMD. This dGPU typically but not always is mounted in a separated board that may or may not be replaced.

That is interesting.

I do run a few Raspberry Pi devices and was aware that memory could be allocated from CPU to GPU but wasn't sure how this was done.

Geoff

---

