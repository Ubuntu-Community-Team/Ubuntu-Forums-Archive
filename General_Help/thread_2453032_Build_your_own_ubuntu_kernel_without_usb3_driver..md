---
title: "Build your own ubuntu kernel without usb3 driver."
date: 2020-11-02
forum: General Help
---

### Post by semo1984 on 2020-11-02
Hello,

First of all, apologies if this post it is not in the right place, but I'm new on the forum and i don't know if it is the right place.

I need to build a ubuntu kernel without usb3 for this issue:
[LIST]
[*][https://acroname.com/blog/why-cant-i-connect-more-usb-30-devices-my-system](https://acroname.com/blog/why-cant-i-connect-more-usb-30-devices-my-system) 
[/LIST]


 I've been trying using ubuntu 19.10 and 20.04 and following this topic over a virtualbox since i don't have yet the computer where this kernel will be placed:
[LIST]
[*][https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel) 
[/LIST]

But I'm facing some difficulties:
[LIST=1]
[*]If i setup my .config without usb3 pops ups the next error message:
[LIST]
[*]FAIL (m != y): CONFIG_USB_XHCI_HCD policy<{'amd64': 'y', 'arm64': 'y', 'armhf': 'y', 'i386': 'y', 'ppc64el': 'y'}> mark<ENFORCED> note<ensures USB 2.0/1.1 probe ordering> flag<REVIEW> (related to annotations file) 
[/LIST]
  
[*]If you remove this conditions, then appears another error related to some missing modules that I've ignored using this compiling command:
[LIST]
[*]LANG=C fakeroot debian/rules DEB_BUILD_OPTIONS=parallel=4 binary-headers binary-generic skipmodule=true skipabi=true 
[/LIST]
  
[*]For ubuntu 19.10 it gives me the next error related to abi, that I've not been able to solve it:
[LIST]
[*]*EE*: *Previous* or *current ABI file missing*! 
[/LIST]
  
[*]For ubuntu 20.04, i had to remove the CONFIG_USB_XHCI from the common files (if not it was still using usb3 driver)
[LIST=1]
[*]debian.master/config/config.common.ubuntu 
[*]Once the 4.1 step is done it compiles. But then any usb is recognized, ehci drivers is not taking over for usb devices 
[/LIST]
    
[/LIST]

I don't know if it is possible to do what i have to do or maybe should i go to an older ubuntu version. But it is important that i get rid of it of the usb3 limitations.

I hope that you can guide me about this issue, but it is important for our current situation.

Best Regards,

Ps. I would like to attach 3 txt files, but i can not do it and i don't know why.

Ps2:
It is failing the attach manager so i'll post the changes directly in the comment.

[B]annotation changes:

[/B]```

+linux (5.4.0-51.57) focal; urgency=medium
+  * Remove xhcdi

```[B]

config.common.amd64:

[/B]```

+CONFIG_USB_ROLES_INTEL_XHCI=n
+#
+# USB Host Controller Drivers
+#
+CONFIG_USB_C67X00_HCD=m
+CONFIG_USB_XHCI_HCD=n
+CONFIG_USB_XHCI_DBGCAP=n
+CONFIG_USB_XHCI_PCI=n
+CONFIG_USB_XHCI_PLATFORM=n
+CONFIG_USB_EHCI_HCD=y
+CONFIG_USB_EHCI_ROOT_HUB_TT=y
+CONFIG_USB_EHCI_TT_NEWSCHED=y
+CONFIG_USB_EHCI_PCI=y
+CONFIG_USB_EHCI_FSL=m
+CONFIG_USB_EHCI_HCD_PLATFORM=y

```

**config.common.ubuntu:**
```

-CONFIG_USB_ROLES_INTEL_XHCI=m
+CONFIG_USB_ROLES_INTEL_XHCI=n
...
-CONFIG_USB_XHCI_DBGCAP=y
-CONFIG_USB_XHCI_HCD=y
-CONFIG_USB_XHCI_HISTB=m
-CONFIG_USB_XHCI_MTK=m
-CONFIG_USB_XHCI_MVEBU=m
-CONFIG_USB_XHCI_PCI=y
-CONFIG_USB_XHCI_PLATFORM=m
-CONFIG_USB_XHCI_RCAR=m
-CONFIG_USB_XHCI_TEGRA=m
+CONFIG_USB_XHCI_DBGCAP=n
+CONFIG_USB_XHCI_HCD=n
+CONFIG_USB_XHCI_HISTB=n
+CONFIG_USB_XHCI_MTK=n
+CONFIG_USB_XHCI_MVEBU=n
+CONFIG_USB_XHCI_PCI=n
+CONFIG_USB_XHCI_PLATFORM=n
+CONFIG_USB_XHCI_RCAR=n
+CONFIG_USB_XHCI_TEGRA=n

```

---

### Post by coffeecat on 2020-11-02
> **semo1984 said:**
> First of all, apologies if this post it is not in the right place, but I'm new on the forum and i don't know if it is the right place.

Welcome to the forum. Each sub-forum has a tagline which describes its purpose. The sub-forum you posted to is for testing official ISOs. Not many people post questions about building custom kernels, so we don't have a specific place for that. Therefore I've moved this to *General Help* in the hope that it will come to the notice of members who can help you. 

> **semo1984 said:**
> 
Ps. I would like to attach 3 txt files, but i can not do it and i don't know why.

Go to the advanced editor and either use the paperclip icon in the toolbar to open the attachment manager, or click on the manage attachments button below the advanced editor.

Alternatively, if the text files are not too large, simply paste the text into your post, but enclose it between BBCode code tags for clarity. Link in my sig for code tags if you need it.

Good luck.

---

### Post by dragonfly41 on 2020-11-02
Intuitively (since I have no experience in the subject) my first thought is to look at [CUBIC]("https://linuxhint.com/customize_ubuntu_iso_create_spin/").
You might be able to knockout usb3.

---

### Post by semo1984 on 2020-11-02
Thanks for answering my question.

I'll check it.

Best Regards!

---

