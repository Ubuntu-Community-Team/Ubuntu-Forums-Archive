---
title: "HowTo - Remove Grub From Vista"
date: 2007-12-21
forum: General Help
---

### Post by techgeek40 on 2007-12-21
If you simply remove the Ubuntu partition, GRUB (Linux boot loader) will still be on your PC (in control).

So you need to restore your Master Boot Record (MBR) for Vista (so that Vista will handle the booting, not GRUB).

Here is how to repair/restore your Master Boot Record (MBR)

1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
2. Press a key when you are prompted.
3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4. Click Repair your computer.
5. Click the operating system that you want to repair, and then click Next.
6. In the System Recovery Options dialog box, click Command Prompt.
7. Type Bootrec.exe /FixMbr, and then press ENTER.

That's it. Now when you reboot your PC, Vista will load automatically... You can now safely boot using your Ubuntu desktop CD, to use the built in Gnome Partition Manager to remove your Ubuntu partition!

---

