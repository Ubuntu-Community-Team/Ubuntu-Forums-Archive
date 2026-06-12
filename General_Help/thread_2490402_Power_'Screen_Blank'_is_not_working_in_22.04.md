---
title: "Power 'Screen Blank' is not working in 22.04"
date: 2023-09-02
forum: General Help
---

### Post by marciano#1 on 2023-09-02
[HTML]lspci -k | grep -EA3 'VGA|3D|Display'[/HTML]
> 00:02.0 VGA compatible controller: Intel Corporation HD Graphics 530 (rev 06)
	DeviceName:  Onboard IGD
	Subsystem: ASUSTeK Computer Inc. HD Graphics 530
	Kernel driver in use: i915


After running [HTML]sudo modprobe amdgpu[/HTML] Screen Blank works (I've set it to 1 minute)
I tested it in a short time.  Then I went to Thunderbird (already opened), moved some mails ant finally I left the computer.
Screen Blank does not work anymore.
Then I started to write here and left the computer for more than a minute and Screen Blank works again.
So it seems to work randomly.
What can I do? I didn't have such issue in 20.04
Thank you

---

### Post by marciano#1 on 2023-09-06
No answers yet.
It seems I have to downgrade to 20.04

---

