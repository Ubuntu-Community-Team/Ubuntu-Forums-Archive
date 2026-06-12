---
title: "No sound after login"
date: 2016-02-06
forum: General Help
---

### Post by David_Medeiros on 2016-02-06
Hello, my sound device is detected since the login screen drumbs play. From there i can move the sound bar normaly. Once i log in it gets stucked on mute and when i go to setings no device is found. This all hapened in the same day i installed intel-linux-driver-installer. Tried to reinstall pulseaudio, alsamixer. Nothing works, I have no idea what to.
Any ideas?

---

### Post by One4All on 2016-02-06
I have no idea but it will help if you use sudo lshw (maybe reduce the output if some of it could reveal a vulnerability) and tell us what hardware you have.  Also it helps if we know what version of Ubuntu you have?

---

### Post by David_Medeiros on 2016-02-06
> **One4All said:**
> I have no idea but it will help if you use sudo lshw (maybe reduce the output if some of it could reveal a vulnerability) and tell us what hardware you have.  Also it helps if we know what version of Ubuntu you have?
Ok so this is the output that lshw gives about my audio device
[HTML]        *-multimedia             description: Audio device             product: 5 Series/3400 Series Chipset High Definition Audio             vendor: Intel Corporation             physical id: 1b             bus info: pci@0000:00:1b.0             version: 05             width: 64 bits             clock: 33MHz             capabilities: pm msi pciexpress bus_master cap_list             configuration: driver=snd_hda_intel latency=0             resources: irq:28 memory:d4400000-d4403fff
[/HTML]
i am using Ubuntu 15.10

---

