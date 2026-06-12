---
title: "On my double-boot computer ubuntu is blocked, windows works."
date: 2017-11-19
forum: General Help
---

### Post by aubertinsylvain on 2017-11-19
Hi all. I was on ubuntu and tried to install launchers. I made a mistake and ubuntu blocked. The only thing I could do was to turn off the PC. Now when I turn on, something like a terminal appears, speaking of "grub". It proposes many commands which I don't know. The only thing I can do is to"exit" and then I have the possibility from there to boot windows 10. That is good enough. But there must be a way to boot ubuntu using one of the commands grub proposes. But what command? Can someone help me ?

---

### Post by oldfred on 2017-11-19
Sounds like grub not fully or completely installed.
What brand/model system? And what video card/chip?
What version of Windows?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by aubertinsylvain on 2017-11-20
When I turn on the PC something like a terminal appears., instead of ubuntu. I insert "exit" in the grub text. A new page appears where I find the 2 boots: ubuntu and windows 10. If I choose Windows, it runs very well. But if I choose ubuntu, it shows me "terminal" once again, Does it mean that the whole ubuntu is broken, and that I shall begin all the work about ubuntu booting ??

---

### Post by ajgreeny on 2017-11-20
No, it does not necessarily mean your Ubuntu is totally broken, particularly when run in dual boot with Windows 10 which has been known to run an important update and remove Ubuntu from the UEFI boot procedure.

There are many other possible reasons for this problem and to help you further we really do need you to follow oldfred's instructions to run Boot-info script, so please do that and report back here the pastebin link you see when it has run.

---

