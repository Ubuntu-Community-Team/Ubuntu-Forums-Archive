---
title: "Login screen not displayed"
date: 2024-05-16
forum: General Help
---

### Post by JulesJacobs on 2024-05-16
When I boot up the computer I am shown a dark grey screen with a mouse cursor, but nothing else. When I short press the power button I see a menu that allows me to power off the computer. When I reboot the computer several times, I am able to get the login screen and use the computer. I would like to have it so that it always shows the login screen, without having to reboot several times. Do you know how to fix this issue? I am using Ubuntu 24.04 LTS.

---

### Post by dragonfly41 on 2024-05-16
Something is broken. 
What is "the computer". Spec?
Try LiveUSB again. Do you see same problem?

Found your last post December 2008 .. might help contributors .. 
[https://ubuntuforums.org/showthread.php?t=1010190](https://ubuntuforums.org/showthread.php?t=1010190)

---

### Post by JulesJacobs on 2024-05-16
Thanks. The usb boots up and works well, and it does not have this problem, but I don't get a login screen there. Spec is Ryzen 7950X with RTX 4090 graphics card, so the specs should be good enough to run, I think. Is there any other information I can provide that may be relevant? Ubuntu is very fast when I am able to log in.

---

### Post by dragonfly41 on 2024-05-17
If you are using Ubuntu 24.04 can you run this command (as a starter for one just to gauge what you have in booting up) ...

efibootmgr

---

### Post by JulesJacobs on 2024-05-17
Running this command produces the following output:

[FONT=Courier New]~$ efibootmgr
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0001
Boot0000* Ubuntu    HD(1,GPT,18121b45-5a92-4fdd-8128-7e61f1cbd7eb,0x800,0x219800)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* CT2000T500SSD8    BBS(HD,,0x0)0000424f[/FONT]

---

### Post by dragonfly41 on 2024-05-17
I'm hoping that others chips in since I see nothing amiss there. You have a pulse.
Now if it were me I would install rEFInd since I'm very comfortable with it.
It sits as a neighbour in \boot\EFI\refind .. alongside \boot\EFI\ubuntu\
and you go into BIOS at boot to set it as choice.
But it might be BIOS update needed at a guess.

---

### Post by #&amp;thj^% on 2024-05-17
Just to add to dragonfly41's suggestion on rEFInd, it's worthwhile to install it.
Grub is always the boot-loader and rEFInd is a boot-manager.

---

### Post by &amp;KyT$0P# on 2024-05-17
> **JulesJacobs said:**
> RTX 4090 graphics card,

Does it help to try a different driver for this Nvidia graphics card?

---

