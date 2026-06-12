---
title: "PCI error after update, can't boot with graphics card"
date: 2021-03-22
forum: General Help
---

### Post by stilson on 2021-03-22
G'day folks,
After updateing 18.04 yesterday my system boots with no visuals if have a monitor pluged in to my GPU card only.
If I boot with a monitor plugged into the mobo (with or without one plugged into GPU) the system boots normally (with visuals).

I get the following error in my log:

> ACPI: \_SB_.PCI0.SBRG.ASOC: Device cannot be configured due to a frequency mismatch

I imagine this error is preventing the GPU working but not entirely sure.

Does anyone have any suggestions?

Kernel:
Ubuntu 4.15.0-139.143-generic 4.15.18

mobo:
P5G41T-M LX

GPU:
GTX 1080ti

Any help would be appreciated. cheers.

---

### Post by ajgreeny on 2021-03-22
Have you tried uninstalling the nvidia driver that you had and then reinstalling whatever is recommended by the Additional Drivers utility?

---

### Post by stilson on 2021-03-22
Thanks mate, I didn't really consider the graphics driver to be a suspect. I am using a proprietry nividia driver so I'll give the Nouveau driver a whirl now.

---

### Post by stilson on 2021-03-22
Actually, on second thoughts, as my current error is resulting in no visuals, I'll have no way of knowing if the driver change causes a problem too, and then I'd be trying to daignose a double no-visuals fault. I think I'll leave that till last.

How sure are you updating the graphics driver would be a possible solution? Any other ideas?

---

### Post by ActionParsnip on 2021-03-22
[https://unix.stackexchange.com/questions/267172/linux-mint-acpi-pcc-probe-and-usb-descriptor-errors-during-boot#268556](https://unix.stackexchange.com/questions/267172/linux-mint-acpi-pcc-probe-and-usb-descriptor-errors-during-boot#268556)

---

### Post by stilson on 2021-03-22
> **ActionParsnip said:**
> [https://unix.stackexchange.com/questions/267172/linux-mint-acpi-pcc-probe-and-usb-descriptor-errors-during-boot#268556](https://unix.stackexchange.com/questions/267172/linux-mint-acpi-pcc-probe-and-usb-descriptor-errors-during-boot#268556)

Thanks AP, That was one of only two search results I found too (the other didn't get answered).
I couldn't really make heads nor tails of it though.
The general gist seems to be that you shouldn't really be getting that error in a previously working configuration, so try moving the card (which I can't do as I only have one PCIe x16 slot). That doesn't really tell me what's gone wrong. Someone then suggests it may be an indicator of 'a more complex hardware problem' which doesn't fill me full of confidence.

Strange it happened after an update.

I've tried booting on an older kernal and still no luck.

---

### Post by stilson on 2021-03-23
G'day folks, and thanks for the help.

I solved the issue by simply re-seating the GPU card.
Before that, I had also tried booting a vanilla 18.04 live install and still no joy, so was able to rule out the recent update breaking something being the cause. The timing was just coincidental.

So my only contribution to others searching for solutions to this uncommon error is that it is indicative of hardware failure.

---

### Post by stilson on 2022-02-03
For anyone else with this issue:

The issue ended up happening gradually more and more often over time, until my mobo eventually failed altogether last week. With each occurrence, wiggling or re-seating the GPU resolved the issue for increasingly lower periods of time until a re-occurrence.

The error does seem to me to be an indication of hardware failure.

---

