---
title: "Virtualbox fails to open a session"
date: 2020-11-12
forum: General Help
---

### Post by josephfg on 2020-11-12
Hi.  I am running Ubuntu 20.04.1 LTS on a HP laptop.

I want to vid chat with someone who only has FaceTime.  I installed Virtualbox from the terminal and downloaded Facetime.  I opened Virtualbox and created a virtual machine to run MacOSX.  It shows up in the left-hand pane, but when I try to start it, it gives the following error.



Failed to open a session for the virtual machine MacOSX.

AMD-V is disabled in the BIOS (or by the host OS) (VERR_SVM_DISABLED).

Result Code: NS_ERROR_FAILURE (0x80004005)
Component: ConsoleWrap
Interface: IConsole {872da645-4a9b-1727-bee2-5585105b9eed}



I'm not even clear on how to get to my BIOS settings, or I would have tried that first.  So if that's where to fix this, how do I get to my BIOS settings?  Or if not, what do I do?  Thanks.

---

### Post by DuckHook on 2020-11-12
MacOS is heavily proprietary and just as heavily silo&#8209;ware/jail&#8209;ware. It is designed to test extensively for Apple HW and run only on legitimate Apple HW. To my knowledge, no one has ever succeeded in running it in a VM without kludges, tricks and sorcery that would make even an über&#8209;geek's eyes water.

Someone else on these forums may be able to point you to some sort of solution, but you shouldn't get your hopes up.

---

### Post by QIII on 2020-11-12
While it is not against Apple's EULA/ToS to install other OSes on Apple hardware, it is against Apple's EULA/ToS to install their OS on non-Apple hardware -- even virtual hardware.

We do not support circumvention of EULA/ToS.

Closed.

---

