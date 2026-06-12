---
title: "black screen after fresh install"
date: 2024-05-31
forum: General Help
---

### Post by rufus009 on 2024-05-31
:D hi!

I installed Linux on my laptop, its a hp fc105; i also installed fedora, and the same thing happends.
first of all, it wont pass the first screen and stays in black (in the instalation procces) i have to close the lid of the laptop and it suspends then it give me signal.

same happen with fedora, i manage to install ubuntu with safemode, but when it boot it boot with black screen, i have to suspend the laptop and the login screen show off.... i just dont want to break the lid for doind that

sorry for my bad english xD, and thanks for the help

i try editing the grub.conf and remove the "quiet splash" and nothing happend i see the log scrolling and then black :(

---

### Post by QIII on 2024-06-02
Moved to **General Help**

---

### Post by oldfred on 2024-06-02
If you had to use Safe boot to boot installer, you probably have nVidia.
And best to select to install the optional/restricted extra drivers so nVidia driver installed as part of normal install.

If you have UEFI Secure Boot on, you also have to provide a MOK-machine owner key as Ubuntu cannot authorize third party drivers as Secure, but a machine owner can. Often easier to turn Secure boot off.

Can you boot to grub menu?
And then select the recovery mode?
If so you can install the nVidia driver from there, by turning & internet & adding driver.
Do not download a driver from nVidia directly.

---

