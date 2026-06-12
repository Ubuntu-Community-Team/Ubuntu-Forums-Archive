---
title: "Ram type &amp; speed"
date: 2021-01-04
forum: General Help
---

### Post by AnupamMitra on 2021-01-04
In one of my Desktops OS is Ubuntu 18.04.5 32 bit. RAM is 2 GB. Processor is Pentium(R) Dual-Core CPU E5200 @ 2.50GHz × 2 . Now I would like to upgrade my OS to Ubuntu 20.04. As I have heard that minimum RAM should be 4 GB for 20.04. Therefore, I would like to increase the RAM. How do I know the required speed of RAM commensurate with my PC for purchasing another one?

---

### Post by CelticWarrior on 2021-01-04
There are different issues to unpack here.
Firstly, you CAN'T upgrade to 20.04 if you have 32-bit hardware. 18.04 is the last LTS release with 32-bit support. After that you need to find a different Linux family of OSes, like Debian, that still support it. For how long is the question to which I have no answer.

4GB of RAM is considered the bare minimum nowadays to a comfortable experience. This isn't related with the 20.04 release specifically.

---

### Post by CatKiller on 2021-01-04
Although you've been running a 32-bit install, that processor is [apparently](https://ark.intel.com/content/www/us/en/ark/products/37212/intel-pentium-processor-e5200-2m-cache-2-50-ghz-800-mhz-fsb.html) 64-bit. So you'll be able to do a fresh install of a 64-bit OS since, as CelticWarrior says, 32-bit can't be upgraded.

You'll need to look in your motherboard's manual to know which RAM you can use. From the vintage it might be DDR2 or DDR3. You'll also be able to see from there what your maximum RAM configuration is. The older types of RAM may be hard to find and expensive; there's a sweet spot of when to buy RAM. When a new type has just been invented, supply is low and prices are high. Then production increases and prices fall. Then production stops, and you can only get them from hoarders, so prices go right up.

---

### Post by GhX6GZMB on 2021-01-04
The E5200 is 64-bit.

---

### Post by TheFu on 2021-01-04
A Q8400 is about 3x faster CPU that will work in the same motherboard. It uses DDR3.

How can I say this nicely. Sometimes RAM upgrades are a bad idea without replacing everything else too.  I probably wouldn't spend $10 to upgrade RAM on a computer that old.

I bet you can find a Q8400 + MB + 8G of RAM for $40 somewhere.  I'd be happy to get $40 for my E6600 + 8G RAM and MB.  One person's junk is another person's goldmine.  If spending $80 is possible, then an off-lease business computer with a Core i5 could be found that is 4-8x faster with plenty of RAM.  And if your case is standard, replacing the MB + CPU +RAM can often been done for $200 total to provide 10x+ more performance.

---

### Post by grahammechanical on 2021-01-04
I am thinking about the video adapter. How much of its own memory does the video card have? It is good that the machine can run Ubuntu 18.04 but Xubuntu or Lubuntu might be more suitable for the video adapter in that machine.

As already suggested at what point does upgrading the parts of a machine become equal in cost to purchasing newer and more powerful, but not the latest hardware.

Regards

---

### Post by GhX6GZMB on 2021-01-04
FYI, $40 can be quite a lot of money in India. Not to mention $80 or even $200. "Flaunting it" is not very nice.

---

### Post by TheFu on 2021-01-04
> **ml9104 said:**
> FYI, $40 can be quite a lot of money in India. Not to mention $80 or even $200. "Flaunting it" is not very nice.

$40 is quite a bit of money to me as well, but I wouldn't assume that someone else couldn't use information regardless of price. Those considerations are for the OP to decide. At least the information was provided, which is often appreciated.

---

### Post by GhX6GZMB on 2021-01-04
> **TheFu said:**
> $40 is quite a bit of money to me as well, but I wouldn't assume that someone else couldn't use information regardless of price. Those considerations are for the OP to decide. At least the information was provided, which is often appreciated.

Fair point.

But the HW race sometimes goes too far. I'm running Lubuntu 20.04 on two 12-year old HP 6910p machines, one with 2 GB, the other with 4 GB, and both run very fast and with no problems at all.
1 GB of RAM (SO-DIMM 666/800) costs around $6 these days. To me it seems an alternative that's a lot cheaper.

---

### Post by Keith_Helms on 2021-01-04
I was looking at adding ram to a system and found the following command told me what type and speed ram is currently in it:

```
sudo dmidecode -t 17
```

For each used memory slot, you'll get a listing like this

```
Memory Device
    Array Handle: 0x001C
    Error Information Handle: No Error
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 16384 MB
    Form Factor: SODIMM
    Set: None
    Locator: ChannelA-DIMM0
    Bank Locator: BANK 0
    Type: DDR4
    Type Detail: Synchronous
    Speed: 2667 MT/s
    Manufacturer: 8945
    Serial Number: 16161616
    Asset Tag: 9876543210
    Part Number: GKE160SO102408-2666 
    Rank: 2
    Configured Memory Speed: 2667 MT/s
    Minimum Voltage: 1.25 V
    Maximum Voltage: 1.5 V
    Configured Voltage: 1.2 V

```

---

### Post by TheFu on 2021-01-04
```
sudo dmidecode -t 17
```
shows the speed being used, not the speed for which the RAM is rated.  For DDR4, even using identical RAM model from the same vendor doesn't mean addon RAM will run at that speed. I'm running at 2800Mhz with RAM that is all rated for 3200Mhz for this reason. Even a little faster and the system is unstable.

 But with DDR3, is was fairly safe IME, even to mix RAM vendors with limits.

I don't recall DDR2 being easy, but memory isn't clear.

---

### Post by Keith_Helms on 2021-01-04
> **TheFu said:**
> ```
sudo dmidecode -t 17
```
shows the speed being used, not the speed for which the RAM is rated.  For DDR4, even using identical RAM model from the same vendor doesn't mean addon RAM will run at that speed. I'm running at 2800Mhz with RAM that is all rated for 3200Mhz for this reason. Even a little faster and the system is unstable.

 But with DDR3, is was fairly safe IME, even to mix RAM vendors with limits.

I don't recall DDR2 being easy, but memory isn't clear.

True, it shows the actual speed the system is running the ram at, but unless you're overclocking that's a good starting point for buying additional memory.

---

### Post by oldfred on 2021-01-04
If you have 2GB of RAM, you have install, just not full Ubuntu as it wants more RAM. 
But what video chip? Some older motherboards are not well supported.

I have 64 bit 20.04 Kubuntu installed in my 2006 laptop which is  Intel(R) Core(TM)2 CPU T5500  @ 1.66GHz with 1.5GB of RAM and uses Intel video. 
Functional, not great, but I have Kubuntu on all my other systems, so want same configuration. 
Tried installing full Ubuntu and it just hung, 16.04 had worked, but really slow until I installed fallback. Did install 20.04 server and added fallback, but took a lot of effort. Kubuntu just worked.

Kubuntu is not particularly lightweight but a bit better than Ubuntu.
Other lightweight versions may be better.
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie
[https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)

---

### Post by Yellow Pasque on 2021-01-05
> How do I know the required speed of RAM commensurate with my PC for purchasing another one? 

Read your motherboard or system manual. Or look at dmidecode and try to figure it out. Or look in BIOS.

> **TheFu said:**
> I probably wouldn't spend $10 to upgrade RAM on a computer that old.

It depends on what you're doing and whether your satisfied with the current performance.
I recently had an Athlon X2 5050 system (similar vintage to OP's system) with 2GB of RAM and it worked fairly well for general use, but the RAM was definitely a bottleneck, especially when web browsing. Adding some more RAM allowed me to put off building a new system until my financial situation was better.

---

### Post by AnupamMitra on 2021-01-06
> **TheFu said:**
> A Q8400 is about 3x faster CPU that will work in the same motherboard. It uses DDR3.

How can I say this nicely. Sometimes RAM upgrades are a bad idea without replacing everything else too.  I probably wouldn't spend $10 to upgrade RAM on a computer that old.

I bet you can find a Q8400 + MB + 8G of RAM for $40 somewhere.  I'd be happy to get $40 for my E6600 + 8G RAM and MB.  One person's junk is another person's goldmine.  If spending $80 is possible, then an off-lease business computer with a Core i5 could be found that is 4-8x faster with plenty of RAM.  And if your case is standard, replacing the MB + CPU +RAM can often been done for $200 total to provide 10x+ more performance.

At this point of time, I'm unable to invest more for changing everything. Cost of only 8GB RAM in India is now equivalent to $54. Changing of Processor and MB is a dream for me. That's the reason I preferred for upgrading RAM.

---

### Post by Yellow Pasque on 2021-01-06
> **AnupamMitra said:**
> At this point of time, I'm unable to invest more for changing everything. Cost of only 8GB RAM in India is now equivalent to $54. Changing of Processor and MB is a dream for me. That's the reason I preferred for upgrading RAM.

That's great, but you still have not told us what system/motherboard you have or showed output from:
```
sudo dmidecode -t 17
```

We cannot answer your question without this information.

---

### Post by AnupamMitra on 2021-02-23
> **Yellow Pasque said:**
> That's great, but you still have not told us what system/motherboard you have or showed output from:
```
sudo dmidecode -t 17
```

We cannot answer your question without this information.

Sorry, I couldn't reply you early due to my sudden and long indisposition. Hope, you won't mind. 

However, I submit the output hereunder.

```

naresh@naresh-G31T-M2:~$ sudo dmidecode -t 17
[sudo] password for naresh: 
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 2.5 present.

Handle 0x000F, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 2048 MB
    Form Factor: DIMM
    Set: None
    Locator: DIMM0
    Bank Locator: BANK0
    Type: SDRAM
    Type Detail: Synchronous
    Speed: Unknown
    Manufacturer: Manufacturer0
    Serial Number: SerNum0
    Asset Tag: AssetTagNum0
    Part Number: PartNum0

Handle 0x0011, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000D
    Error Information Handle: Not Provided
    Total Width: Unknown
    Data Width: Unknown
    Size: No Module Installed
    Form Factor: DIMM
    Set: None
    Locator: DIMM1
    Bank Locator: BANK1
    Type: Unknown
    Type Detail: Unknown
    Speed: Unknown
    Manufacturer: Manufacturer1
    Serial Number: SerNum1
    Asset Tag: AssetTagNum1
    Part Number: PartNum1

naresh@naresh-G31T-M2:~$ 

```

---

