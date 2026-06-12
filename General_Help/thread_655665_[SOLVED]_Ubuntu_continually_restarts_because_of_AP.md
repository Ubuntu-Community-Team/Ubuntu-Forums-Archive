---
title: "[SOLVED] Ubuntu continually restarts because of APIC error"
date: 2008-01-01
forum: General Help
---

### Post by inktri on 2008-01-01
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode. I also believe this is a 64-bit problem because my 32-bit Live-CD works perfectly

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence (strange thing is this has worked a couple of times out of 50+ restarts, I managed to boot into the Live-CD with this method and I was able to install Ubuntu)
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.


Does anyone know how to remedy this problem -- it's so frustrating :(? Do I have to change some motherboard setting? Why does the noapic nolapic work only sometimes? What's wrong with my APIC? 

Thank you very much for the help

---

### Post by inktri on 2008-01-01
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode. I also believe this is a 64-bit problem because my 32-bit Live-CD works perfectly

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence (strange thing is this has worked a couple of times out of 50+ restarts, I managed to boot into the Live-CD with this method and I was able to install Ubuntu)
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.


Does anyone know how to remedy this problem -- it's so frustrating :(? Do I have to change some motherboard setting? Why does the noapic nolapic work only sometimes? What's wrong with my APIC? 

Thank you very much for the help

---

### Post by inktri on 2008-01-01
My 64-bit Ubuntu 7.10 keeps on rebooting while trying to load on startup. This problem exists for everything: trying to start Ubuntu via the Live-CD, via hard drive, via recovery mode. I also believe this is a 64-bit problem because my 32-bit Live-CD works perfectly

I've checked the threads on these forums and have tried what people have suggested with little success:
> 1. appending noapic nolapic nosplash to boot sequence (strange thing is this has worked a couple of times out of 50+ restarts, I managed to boot into the Live-CD with this method and I was able to install Ubuntu)
2. updating my BIOS
3. appending noapic nolapic
4. appending noapic
5. acpi=off
6. acpi=ht


My relevant computer specs:
> 64bit Ubuntu 7.10, Gigabyte P35-DS3L (with latest BIOS), Q6600, GeForce 8400GS, LSI 21320 SCSI hba, 2x Hitachi 15k300 Ultrastar hard drives.

During bootup I'm getting:
> Inquiring remote APIC #2...
... APIC #2 ID: failed
... APIC #2 VERSION: failed
... APIC #2 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 2/3 APIC 0x1
Not responding.

Inquiring remote APIC #3...
... APIC #3 ID: failed
... APIC #3 VERSION: failed
... APIC #3 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.

Inquiring remote APIC #1...
... APIC #1 ID: failed
... APIC #1 VERSION: failed
... APIC #1 SPIV: failed
SMP alternatives: switching to SMP code
Booting processor 3/2 APIC 0x1
Not responding.


Does anyone know how to remedy this problem -- it's so frustrating :(? Do I have to change some motherboard setting? Why does the noapic nolapic work only sometimes? What's wrong with my APIC? 

Thank you very much for the help

---

### Post by inktri on 2008-01-02
ANyone know?

---

### Post by inktri on 2008-01-02
ANyone know?

---

### Post by inktri on 2008-01-02
anyone know?

---

### Post by inktri on 2008-01-04
my solution was to disable "Enable USB mouse/keyboard" from my motherboard bios

---

### Post by Magellan on 2008-01-05
I just started having a phantom rebooting problem.  My motherboard only supports a USB Mouse/Keyboard, so disabling that is not really an option, unless this is just a power saving feature.

I'm using a Logitech wireless keyboard and mouse and am wondering if the batteries in the mouse are weak and maybe the cause of the problem.

Any thoughts?

---

### Post by jobah on 2008-04-14
I have similar motherboard Gigabyte G33-DSR3, ubuntu 7.10 64bit and Quad core Q6600... lost several days, system only worked with nosmp and noacpi.... but when I have disabled just USB mouse, only noacpi is required to boot with all 4 cores... any idea how to solve the rest of the problem? (enable acpi)

I do not understand the connection of smp problem with usb mouse bios support??!

---

### Post by Knertified on 2008-04-19
I'm not sure why this thread is considered "solved" when the problem isnt. I also have this problem on my Gigabyte GA-EP35C-DS3R with Intel Q6600. As stated above the only way to get around this issue is to disable usb keyboard/mouse support. The problem with doing that is that I can no longer choose a selection on the Grub boot menu. I have also updated my bios software to the latest edition.

Hopefully there is some sort of a fix soon! :)

---

### Post by merville on 2008-04-28
Am suffering the same problem too - the only solution so far is to use a PS/2 keyboard with the USB keyboard and mouse support disabled.

If anyone knows of a fix it would e much appreciated

---

