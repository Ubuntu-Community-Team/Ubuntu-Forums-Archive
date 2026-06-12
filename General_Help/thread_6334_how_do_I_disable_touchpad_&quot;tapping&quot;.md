---
title: "how do I disable touchpad &quot;tapping&quot;?"
date: 2004-11-27
forum: General Help
---

### Post by cyberwave on 2004-11-27
I have a Dell 5150 and the proprietary synaptics touchpad that came with it.  The thing is, I never use tapping and the automatic double click drag and stuff is on.  I end up making more mistakes.  How do I turn it off/on?  Customize?  I'm mainly concerned with turning it off.

---

### Post by knappen on 2004-11-27
If you search this forum you will find that others have had the same question.

Edit the file etc/X11/XF86Config-4

Add 
Option         "TapButton1"       "0"

under your synaptic section.

---

