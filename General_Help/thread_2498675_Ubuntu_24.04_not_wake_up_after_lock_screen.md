---
title: "Ubuntu 24.04 not wake up after lock screen"
date: 2024-06-23
forum: General Help
---

### Post by cuonguq on 2024-06-23
Hi everyone,
Today I installed Ubuntu 24.04 on dell latitude 5490, but I discovered a problem.
After pressing the Super+L key combination, my screen goes dark, and I can’t wake up the laptop even though the power button light is still on.
+ I’ve tried pressing various keys on the keyboard, but the laptop remains unresponsive. I have to hold down the power button for 5 seconds and restart the machine.
+ I've tried disable TPM or secure boot or enable usb wake in bios.
+ I've tried edit /etc/default/grub, changing the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```[FONT=var(--ff-mono)]to[/FONT]
```
[FONT=var(--ff-mono)]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash rdrand=force"[/FONT]
```[FONT=var(--ff-mono)]and
[/FONT]
```
[FONT=var(--ff-mono)]sudo update-grub[/FONT]
```
[FONT=var(--ff-mono)]then reboot.[/FONT][FONT=var(--ff-mono)]=>But it's not working[/FONT]

[FONT=var(--ff-mono)]My current setting:
[/FONT]
```
[FONT=var(--ff-mono)]Dim Screen: On
Screen Blank: Never
Automatic Power Saver: On
Automatic Suspend: 15 min
Power Button Behavior: Suspend[/FONT]

```
Does anyone know how to fix this issue? Please help me, thank you very much.

---

### Post by tea for one on 2024-06-24
Try this (although my PC is a Desktop, not a laptop)

While the screen is dark, start typing your login password.
A dialogue box should appear showing how many characters you have entered.
Continue entering your password and hit the Enter key.

The suspend/lock screen implementation in Gnome 46 is not completely perfect.

---

### Post by him610 on 2024-06-24
@quonguq

Could you please explain, *rdrand=force*?

I could find no reference to *rdrand* in the repository

---

