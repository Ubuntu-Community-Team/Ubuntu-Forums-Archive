---
title: "CMOS Security Options"
date: 2014-07-31
forum: General Help
---

### Post by Rytron on 2014-07-31
Hi.

Can I disable some or all options on this section of CMOS? What would be the benefits and disadvantages if any?

---

### Post by tgalati4 on 2014-08-01
What does TPM stand for?  Does this computer have a fingerprint scanner?  You can probably disable them if your computer is in a secure location and you are not worried about it walking off.

---

### Post by Rytron on 2014-08-01
> **tgalati4 said:**
> What does TPM stand for?  Does this computer have a fingerprint scanner?  You can probably disable them if your computer is in a secure location and you are not worried about it walking off.

Hi tgalati4.

Trusted Platform Module as far as I know.
The laptop has no fingerprint scanner.
What does each category in the image do?

---

### Post by sammiev on 2014-08-01
Usually you get a book about the motherboard and what the CMOS options are and do. I do not seem to have those options on mine unless they call them something else. What are the specs on your computer?

---

### Post by Rytron on 2014-08-01
> **sammiev said:**
> Usually you get a book about the motherboard and what the CMOS options are and do. I do not seem to have those options on mine unless they call them something else. What are the specs on your computer?

[http://mysn.eu/schenker-m704#2](http://mysn.eu/schenker-m704#2)

---

### Post by sammiev on 2014-08-01
> **Rytron said:**
> [http://mysn.eu/schenker-m704#2](http://mysn.eu/schenker-m704#2)

Gives you info about the motherboard. :(

---

### Post by Rytron on 2014-08-02
> **sammiev said:**
> Gives you info about the motherboard. :(

I don't know what the mobo is, that is make etc.

---

### Post by Rytron on 2014-08-02
Hi sammiev.

Here's an excerpt from a Sysinfo Report:

[I]MOTHERBOARD
	Host bridge
		Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
		Subsystem: CLEVO/KAPOK Computer Device 6501
	PCI bridge(s)
		Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
	ISA bridge
		Intel Corporation HM86 Express LPC Controller (rev 05)
		Subsystem: CLEVO/KAPOK Computer Device 6501[/I]

---

### Post by sammiev on 2014-08-02
> **Rytron said:**
> Hi sammiev.

Here's an excerpt from a Sysinfo Report:

[I]MOTHERBOARD
	Host bridge
		Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
		Subsystem: CLEVO/KAPOK Computer Device 6501
	PCI bridge(s)
		Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5) (prog-if 00 [Normal decode])
		Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5) (prog-if 00 [Normal decode])
	ISA bridge
		Intel Corporation HM86 Express LPC Controller (rev 05)
		Subsystem: CLEVO/KAPOK Computer Device 6501[/I]

This is what I found on TPM.

Trusted Platform Module:

[https://en.wikipedia.org/wiki/Trusted_Platform_Module](https://en.wikipedia.org/wiki/Trusted_Platform_Module)

[http://www.wave.com/support/trusted-platform-module-tpm-disabled-unavailable-or-locked-0](http://www.wave.com/support/trusted-platform-module-tpm-disabled-unavailable-or-locked-0)

---

### Post by tgalati4 on 2014-08-02
Oh yes, now I remember TPM.  It's like a bad dream.  You want to turn those features off.

---

### Post by Rytron on 2014-08-03
> **tgalati4 said:**
> Oh yes, now I remember TPM.  It's like a bad dream.  You want to turn those features off.

Is there any downside/disadvantage to disabling them?

---

### Post by Rytron on 2014-08-03
Do I need TPM enabled to continue using LUKS (which I am currently using)?

The mobo is an **ASUS P8H77-V LE**.

---

