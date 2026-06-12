---
title: "How to dual boot Windows on Ubuntu?"
date: 2019-10-14
forum: General Help
---

### Post by ranice on 2019-10-14
Hello all, I have just recently built a PC, however as I had not bought windows yet, I decided to use Ubuntu as my primary OS first. Now that I have bought windows, does anyone know how I can dual foot from the Ubuntu side (i.e. create a partition) to install windows onto my PC? 

I have tried my best to google on this issue however I keep getting tutorials on how to dual boot ubuntu on windows which is the opposite of what I am trying to do....

Thanks all in advance for the responses.

---

### Post by mikewhatever on 2019-10-14
There is no way to "dual boot Windows on Ubuntu". The two are separate and independent.
With that out of the way, here is a simple guide to install Windows after Ubuntu, and set up dual boot.
[https://www.linuxdeveloper.space/install-windows-after-linux/](https://www.linuxdeveloper.space/install-windows-after-linux/)

---

### Post by HermanAB on 2019-10-14
Make a virtual machine, then you can run Windows in a window.

---

### Post by ranice on 2019-10-14
> **mikewhatever said:**
> There is no way to "dual boot Windows on Ubuntu". The two are separate and independent.
With that out of the way, here is a simple guide to install Windows after Ubuntu, and set up dual boot.
[https://www.linuxdeveloper.space/install-windows-after-linux/](https://www.linuxdeveloper.space/install-windows-after-linux/)

thanks so much!! I shall try this

---

### Post by oldfred on 2019-10-14
Big difference if UEFI or BIOS.
And if hardware is UEFI and you installed Ubuntu in BIOS boot mode, you may want to think about re-installing.

How you boot install media, UEFI or BIOS is then how it installs for both Windows & Ubuntu.
And Windows only boots in UEFI mode from gpt partitioned drives, so if you install Windows in UEFI mode, it may erase a MBR drive.
Windows only boots in BIOS mode from MBR drives, so may erase or not install to gpt partitioned drive.

Both Windows & Ubuntu must be in same boot mode if on one drive. And should be same mode even if using multiple drives.

---

