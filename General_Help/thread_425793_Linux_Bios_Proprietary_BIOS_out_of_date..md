---
title: "Linux Bios? Proprietary BIOS out of date."
date: 2007-04-27
forum: General Help
---

### Post by Toadmund on 2007-04-27
Apparently my Phoenix BIOs needs to be updated, but I'll be damned, it's M$ friendly, but not Linux friendly it seems.
Is replacing it with Linux BIOS a good idea?
[http://linuxbios.org/Welcome_to_LinuxBIOS]("http://linuxbios.org/Welcome_to_LinuxBIOS")
Will it screw me up and #^%# my computer?
What would I be getting into here?

---

### Post by ramjet_1953 on 2007-04-28
Is your PC working OK?

If it is, leave the BIOS well alone.

You know the old addage "If it isn't broken, don't fix it"

BIOS upgrades are fraught with danger and if something goes wrong, you can be left with a very dead motherboard.

Regards,
Roger :cool:

---

### Post by Toadmund on 2007-04-28
Everyone has a reason, mine is weird crashing once or twice a day.

---

### Post by Computer Guru on 2007-04-28
> **Toadmund said:**
> Apparently my Phoenix BIOs needs to be updated, but I'll be damned, it's M$ friendly, but not Linux friendly it seems.
....
What would I be getting into here?

BIOS is platform-independant. There technically is no such thing as a "Windows Friendly" or "Linux Friendly" BIOS so long as it implements features according to the standards (ACPI, etc.) - Phoenix does.

What you are describing sounds like a hardware failure, typically brought on by dying (old) capacitors.. Not a firmware error.

---

### Post by sir4taye on 2008-02-18
Model: Presario f700 (f730us)
Processor: amd64 tk-55 1.6Ghz
Wireless Card: Broadcom 4311 mini-pci
Graphics Card: nVidia GeForce 6100 (64Mb shared mem)
Gutsy Tribe (Version): 7.10
Boot Parameters: noapic nolapic

So does a fresh ubuntu 7.10 install change or update a bios? I have tri-boot xp/vista/ubuntu. I'd like to know if this distro could've caused a change in my laptops ability to run/start from battery. If I unplug mid use it dies. 
I have learned enough finally to abandon the m$ as soon as this winter term is over. I want to know if this install could've screwed my bios or battery. I'm dealing with warranty people and am worried they will blame it all on ubuntu and don't want to be liable to pay for their faulty hardware. Can they say ths install voids my warranty. I'll fight 'em but I guess I need to know if my bios could've been changed by a normal noapic nolapic install

---

### Post by pointone on 2008-02-18
Linux doesn't do anything with your BIOS until you tell it to. Furthermore, there's no way installing an operating system of your choice should void your *hardware* warranty.

This entire topic is qutie misleading. sir4taye; your problem sounds simply like a failing battery... which is very common. All laptop batteries fail after some time (usually around three years, in my experience). Unfortunately, batteries are not often covered by warranty because of this.

In the OP's case, as already said, BIOSs are platform-independent. BIOS updaters/installers, however,  are usually only available for DOS/Windows. DOSBox/FreeDOS can get around this problem, though.

---

### Post by sir4taye on 2008-02-18
the whole system is only 4 months old, but they're sending a replacement battery under warranty, I just hope thats gonna fix, and it's not some internal capacitor or somethelike. I fear getting taxed and hornswaggled out of warranty service by those in bed with M$ for running another os. Might sound stupid, but I see that kind of ill-will practices by M$ cohorts often. Like opera on m$ failing on google sites, but only after they filed suit against M$ in EU. Am I still sounding lame? Does any other see some of the same with other programs?

---

### Post by Anduu on 2008-02-18
BIOS upgrades are not to be taken lightly.Be sure to eliminate any hardware problems first.Check your RAM,check your power supply,make sure everything is connected securely,make sure you aren't overheating...the list goes on...

***Anything*** can crash your computer...bad software,bad hardware,gremlins....one boo boo with a BIOS upgrade and your motherboard is toast.Trust me I know :( Only update as a very last resort.

As others have said there is no such thing as an OS friendly BIOS.I wouldn't even consider using a third party BIOS update.

---

