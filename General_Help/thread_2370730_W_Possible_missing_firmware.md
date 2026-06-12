---
title: "W: Possible missing firmware"
date: 2017-09-06
forum: General Help
---

### Post by nanobot90 on 2017-09-06
Hello Guys, 

I just migrated to Linux (Ubuntu 16.04) from Windows recently, and I fit the definition of a complete newbie in anything Linux. I installed Ubuntu 16.04 a couple days back, and every time I want to update my system using, 
```
apt-get upgrade
```

it returns the following error,
```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.8.0-36-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915

```

while 
```
apt-get update
```

works fine. I tried,
```
apt-get -f install
apt-get install --fix-missing
```

but they don't fix the problem.

Any help is appreciated :D

---

### Post by vasa1 on 2017-09-06
Do you see```
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
update-initramfs: Generating /boot/initrd.img-4.8.0-36-generic
W: Possible missing firmware /lib/firmware/i915/kbl_dmc_ver1_01.bin for module i915
W: Possible missing firmware /lib/firmware/i915/kbl_guc_ver9_14.bin for module i915
W: Possible missing firmware /lib/firmware/i915/bxt_guc_ver8_7.bin for module i915 
```***every*** time you run```
sudo apt-get upgrade
```after running```
sudo apt-get update
``` or did you see it just the one time?

Also, please post the output of```
lspci | grep VGA
```

---

### Post by nanobot90 on 2017-09-06
Thanks Vasa1. Yeah, every single time I run the command. 

```
lspci | grep VGA
```
Returns the following, 

> 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Seymour [Radeon HD 6400M/7400M Series] (rev ff)


---

### Post by Doug S on 2017-09-06
Yes, you will get these messages.

The issue is that Ubuntu is lagging behind what the Kernel wants for firmware versions.

Note that is doesn't matter unless you actually have one of those Intel processors (Kaby Lake or Sky Lake or the other one I can not remember the name), otherwise you can ignore the warnings.
You might also find other references with an obsolete link to where to get the firmware, because Intel changed it a few months ago.
see also [here]("https://askubuntu.com/questions/811453/w-possible-missing-firmware-for-module-i915-bpo-when-updating-initramfs/811487#811487") (which has the proper link).

---

### Post by nanobot90 on 2017-09-06
Thanks Doug S, 

> **Doug S said:**
> Note that is doesn't matter unless you actually have one of those Intel processors (Kaby Lake or Sky Lake or the other one I can not remember the name), otherwise you can ignore the warnings.

I don't really know how to check if my system's using one of those intel microarchitectures. I read the link, it outlined the two you mentioned and a third Broxton.

I guess I'm just going to ignore this warning like you said. TY

---

### Post by Doug S on 2017-09-06
> **nanobot90 said:**
> I don't really know how to check if my system's using one of those intel microarchitectures.
Do this:
```
$ [COLOR="#FF0000"]cat /proc/cpuinfo | grep "model name"[/COLOR]
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
model name      : Intel(R) Core(TM) i7-2600K CPU @ 3.40GHz
```

My processor is relatively old, I think its Intel marketing name was Sandy Bridge or something, but *NOT* one I have to worry about in terms of those warning messages.

---

### Post by nanobot90 on 2017-09-07
> **Doug S said:**
> Do this:
```
$ [COLOR=#FF0000]cat /proc/cpuinfo | grep "model name"[/COLOR]
```


Thanks Doug. 
No, not that. I do know my processor is Core i5 with a clock-speed of 2.67GHz. I was actually asking if there was a way to check my **Processor Codename**, like you said, 
> I think its Intel marketing name was **Sandy Bridge** or something...

Sorry if this is getting lengthy. I'm just trying to get my head around this thing.:o

---

### Post by him610 on 2017-09-07
I don't know how open you are to visiting the Intel site, [http://ark.intel.com/#@Processors]("http://ark.intel.com/#@Processors"), but you can find the code name of your CPU there if you know the model number, ie i5-6300

---

### Post by Doug S on 2017-09-07
> **nanobot90 said:**
> No, not that. I do know my processor is Core i5 with a clock-speed of 2.67GHz. I was actually asking if there was a way to check my **Processor Codename**, like you said,Well, my plan was to decode it for you based on the model number, but I see now that him610 gave a link to the decoder page (which I didn't previously know about).

Anyway, for example:
i5-6??? is Sky Lake, Abbreviation skl
i5-7??? is Kaby Lake, Abbreviation kbl
Broxton, I don't know.

---

### Post by nanobot90 on 2017-09-07
Gotcha! 
Thanks a lot guys for clearing these things up &#128522;

---

### Post by w-sky on 2018-07-21
Actually ignoring is not a good solution if your CPU does needs those firmware drivers. The guide to the perfect solution is here: [https://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings](https://askubuntu.com/questions/832524/updated-kernel-to-4-8-now-missing-firmware-warnings)

---

### Post by Irihapeti on 2018-07-21
Go to sleep, old thread.

---

