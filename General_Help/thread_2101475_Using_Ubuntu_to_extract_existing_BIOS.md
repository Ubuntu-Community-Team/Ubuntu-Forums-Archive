---
title: "Using Ubuntu to extract existing BIOS?"
date: 2013-01-04
forum: General Help
---

### Post by KingNeil on 2013-01-04
What I want to do is.. extract an image/bin/whatever format it's in... I want the raw data of my BIOS... and I want a Linux/Ubuntu command in order to do it.

I have tried using Flashrom, but it doesn't support my BIOS...

Flashrom has a nice command

flashrom --read filenamehere.bin

But again... it doesn't support my BIOS... so... does anyone know any command/program I can use... in order to extract a complete copy of my BIOS... it doesn't even matter to me which format it's in... I just want the raw data... in its entirety. Thanks

---

### Post by rnerwein on 2013-01-05
> **KingNeil said:**
> What I want to do is.. extract an image/bin/whatever format it's in... I want the raw data of my BIOS... and I want a Linux/Ubuntu command in order to do it.

I have tried using Flashrom, but it doesn't support my BIOS...

Flashrom has a nice command

flashrom --read filenamehere.bin

But again... it doesn't support my BIOS... so... does anyone know any command/program I can use... in order to extract a complete copy of my BIOS... it doesn't even matter to me which format it's in... I just want the raw data... in its entirety. Thanks
hi
i'm not sure but may be these commands can help you:

biosdecode (8)       - BIOS information decoder
intel_bios_dumper (1) - Saves the Intel video BIOS contents to a file.
intel_bios_reader (1) - Parses an Intel BIOS and displays many of its tables

cheers

---

### Post by KingNeil on 2013-01-05
BIOSDecode is just a list of basic info about the BIOS, not the data itself.

I don't have an Intel BIOS, so the Intel tools are not useful.

Anyone else?

---

