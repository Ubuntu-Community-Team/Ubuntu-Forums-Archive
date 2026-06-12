---
title: "[SOLVED] Video Card Driver Help ATI"
date: 2008-06-04
forum: General Help
---

### Post by czechman86 on 2008-06-04
I just recently installed Kubuntu as I got tired of messing up my Arch installs and wanted something that I couldn't play around with as much and was unable to have the system configure my video card driver. The reason for this was I was running an update and it said another package manager was in secession. After the update finished I clicked yes on the dialog box in order to start the other package manager that would download the proper driver for my video card. Well it crashed and no dialogs have appeared since. There is an option on the screen configure page as to which drivers I can download, and to be honest, there are tons of choices for ATI. I was wondering if anyone could help me fast track this process.

Here is the output for lspci:

```
czechman86@uBox:~$ lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc RS690 [Radeon X1200 Series]

```

I am thinking that the proper driver to use would be the ATI Radeon (fglrx) driver.
Thanks in Advance!

---

### Post by czechman86 on 2008-06-04
yup that did it.

---

