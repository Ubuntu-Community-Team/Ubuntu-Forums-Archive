---
title: "ASUS laptop A53B with TWO Radeon cards not working"
date: 2018-06-06
forum: General Help
---

### Post by martinmolema on 2018-06-06
Hi all,

I seem to lack permission to log a thread in the Hardware section, so hopefully you can help me using this thread. I have been searching the forum for a solution, but mine seems to be weirder than things I already found. I have been given an ASUS A53B laptop with TWO Radeon cards. It seems to be a Hybrid system, but usually it's a hybrid with two different brands like InteL + AMD. Mine says:
martin@venus:~$ xrandr --listproviders 
Providers: number : 0
martin@venus:~$ sudo lshw -c display
[sudo] wachtwoord voor martin: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Wrestler [Radeon HD 6310]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b0000000-bfffffff ioport:f000(size=256) memory:feb00000-feb3ffff memory:c0000-dffff
  *-display UNCLAIMED
       description: VGA compatible controller
       product: Seymour [Radeon HD 6400M/7400M Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller cap_list
       configuration: latency=0
       resources: memory:c0000000-cfffffff memory:fea20000-fea3ffff ioport:e000(size=256) memory:fea00000-fea1ffff

Only way to boot the system is by shutting down the Radeon driver in the GRUB Boot options (radeon.modeset=0). Then I get this poor resolution, but at least enables me to do some investigations.
(EDIT) :: forgot to mention that there is no option in BIOS to disable either card


How to proceed? It's a nice laptop with a huge SSD (240GB); not all too fast, but way better than the original Win10 installed when I received it.

By the way: I got this serious warning on UEFI installation..... I declined it, but what's the difference? Tried to read some material, and it appears I do not have a real BIOS anymore? But what is this thing I can enter before real startup?

Greetings and any help is really appreciated, so this laptop can help my kids do some homework :)
Martin

---

### Post by Yellow Pasque on 2018-06-07
> **martinmolema said:**
> Only way to boot the system is radeon.modeset=0

What happens when you try to boot without nomodeset?

> By the way: I got this serious warning on UEFI installation..... I declined it, but what's the difference? Tried to read some material, and it appears I do not have a real BIOS anymore? But what is this thing I can enter before real startup?

Be more specific. I'm not sure what you're talking about and I don't know if anyone else can figure out what warning you're referring to from your description.

---

### Post by martinmolema on 2018-06-07
If I remove the nomodeset then the boot process freezes after a while. I have UbuntuGnome, and this displays a rotating icon which simply stops. 

Regarding the UEFI boot: when selecting the device I want to install Ubuntu on, there is this dialog that asks "Are you sure to erase ... bla bla". I'm not completely sure, but after that it asked "If you want to be able to install a different operating system in the future, then stop here to prevent UEFI boot installation" or something of that kind.

---

### Post by martinmolema on 2018-06-07
Regarding UEFI-boot:Just found this article ([https://help.ubuntu.com/community/UEFI);](https://help.ubuntu.com/community/UEFI);) apparently yesterday night I was not hitting the right keys on my keyboard to find this....

---

### Post by basse2 on 2019-04-20
did you ever manage to get this working? 
I have a similar laptop, maybe even the same.. with same problem... 
interestingly, Manjaro linux seems to work fine.. but Xubuntu (that I wanted) throws out errors of modesetting not available for the driver (radeon)..

.b

---

