---
title: "Is it possible to run ubuntu 13.04 without Compiz?"
date: 2013-08-06
forum: General Help
---

### Post by fparri on 2013-08-06
I tried ubuntu 13.04. I like it but, ufortunately, from time to the desktop hangs due to a crash in compiz. is it possible to run ubuntu standard unity desktop without Compiz?

---

### Post by fparri on 2013-08-06
I tried ubuntu 13.04. I like it but, ufortunately, from time to the desktop hangs due to a crash in compiz. is it possible to run ubuntu standard unity desktop without Compiz?

---

### Post by fparri on 2013-08-06
I tried ubuntu 13.04. I like it but, ufortunately, from time to the desktop hangs due to a crash in compiz. is it possible to run ubuntu standard unity desktop without Compiz?

---

### Post by howefield on 2013-08-06
Threads merged.

One is truly sufficient.

---

### Post by grahammechanical on 2013-08-06
The answer is NO. Unity is a Compiz plugin. Compiz is the Window Manager/Compositor of standard Ubuntu+Unity. Disabling the Unity plugin will break the desktop. Uninstalling Compiz, as some have done, will break the desktop.

As part of the development of Ubuntu on mobile devices a different display server is being developed (MIR). We might see MIR replace Compiz in April 2014. The first part of this change over is about to be put in place - Xmir. And will be standard in 13.10. We can install Xmir in 13.10 through a PPA. I have been runiing 13.10+Xmir since the first week of July. And yesterday a Xubuntu 13.10 ISO image was released for testing that installs Xmir. I am posting from it now. The main issue is the lack of proprietary video driver support. It only works with the Nouveau open source video driver at present.

Regards.


[https://wiki.ubuntu.com/Mir/](https://wiki.ubuntu.com/Mir/)

---

### Post by ajpat3 on 2013-08-06
Thank you.

---

### Post by dcstar on 2013-08-07
> **grahammechanical said:**
> The answer is NO.
........

Rubbish, you install the **gnome-session-fallback** package and then log in with the "Gnome Classic (no effects)" selection. That does not use the Compiz features.

---

### Post by gleedadswell on 2013-08-07
> **dcstar said:**
> Rubbish, you install the **gnome-session-fallback** package and then log in with the "Gnome Classic (no effects)" selection. That does not use the Compiz features.

OK, so you can run ubuntu without compiz.  But the original question was whether you could run the unity desktop without compiz, to which the answer is no.

---

