---
title: "ACPI: DMI BIOS year==0, assuming ACPI-capable machine"
date: 2007-11-22
forum: General Help
---

### Post by CarlosAtaide on 2007-11-22
Hi everyone!

I've been using Ubuntu for some time now and have been really happy with it! But I can't install Gutsy. Every variant of the 7.10 Ubuntu I can't install it.

ACPI: DMI BIOS year==0, assuming ACPI-capable machine

This is the error displayed, and after that the Live CD won't do anything. It looks like it's loading but after some time, it starts to display some errors. I have tried with:
Ubuntu 7.10
Xubuntu 7.10
Fluxbuntu 7.10
gOS (based on Ubuntu 7.10)

I have once attempted to do a roundabout of this by upgrading to 7.10 with the Internet updates, but the result is the same. The installer was successful, but I wouldn't start Ubuntu.
However, If in the GRUB boot options I'd choose the earlier version of Ubuntu (Feisty) then it would start normally with no problems.

On Edgy, and Feisty I have never encountered any problems of this sort. Can anyone help me with this? 

I have already disabled ACPI in the BIOS but it made no difference.

---

### Post by Pelonchas on 2007-12-17
In pretty new in using Ubuntu but i think this happen to me in 5.10 version.
In the first screen when you boot with the Live Cd, you need to press f7 i can't remember, search for the other options button. There's gonna appear a command line to pass to the kernel, try writting at the end acpi=off and ENTER. If it doesn't work try acpi=force. Try these ones.

---

### Post by Neovos on 2008-02-11
Looks like it thinks your machine is too old for acpi support. To finesse acpi a little more then "on or off" check this out 

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) 

What just happened to me was that it default boot did nothing, acpi=off worked, but disabled my hyperthreading and prolly lots of other things I wanted, and "irqpoll" worked but took forever to boot and slowed lots of things down and caused all kinds of errors when it started. So I figured that it was a irq hardware thing with my acpi. So I settled on the "acpi_irq_balance" option and it worked perfectly.

---

