---
title: "BIOS Concerns"
date: 2007-03-19
forum: General Help
---

### Post by neverwhere on 2007-03-19
Hello. I'm hoping someone could illuminate me with something I am having an issue with. 

I have been running edgy without issue and have even upgraded to feisty without any issues. My concerns stem from later kernel revisions (currently 2.6.20.12-generic). Prior to this latest version I had undergone several kernel updates as necessary when Update Manager indicated things were out of date with an explanation to follow. 

Upon rebooting to 2.6.17.11-generic I saw a kernel panic ```
ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
``` and things would hang on boot. So after entering GRUB and adding the required tag I could boot without issue. Fine.

My issue is tonight I obtained an updated bios and flashed it. The bios revision date during POST states 08/12/2002 however I still get the ACPI kernel panic detecting the BIOS as still being out of date. Confirming this, I ran dmidecode from console with the following output:

```
BIOS Information
        Vendor: American Megatrends Inc.        
        Version: 062710                          
        Release Date: 07/15/97                        
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 256 kB
```

My mobo's manufacturer's website even lists the revision ([taken from here]("http://www.pcchipsusa.com/support-pcchips-bios.asp")) as:

Product name: M817LMR
Chipset: Alimagic
Bios Type: AMI
BIOS File Name: 817_020812S.ZIP (08/12/02) 

Have I overlooked something? Is this correctable? Does the kernel hold outdated info that can not be re-detected? I have what I consider to be a pretty good grasp on hardware and software (but sometimes fickle things like BIOS' and kernel idiosyncrasies elude me now and again) and I have been fairly keen with various Linux distros over the years however I am admittedly nowhere near a guru but I can keep my system workable. I am hoping someone can point me in a direction and help me realize my situation better so that I can make sense of this. 

Motherboard: PCChips M817LMR
CPU: AMD Athlon 1200
RAM: 1 GB

Thanks in advance to anyone who may be able to provide any information.

---

### Post by egar on 2007-04-09
I had a similar problem.  You might try booting with the option of acpi=force.  If that works for then you can add that as a permanent option to /boot/grub/menu.lst.

For my older 1999 laptop BIOS, this works just fine.

---

