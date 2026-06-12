---
title: "Ubuntu 22.04 Screenshot utility not storing image to traditional clipboard"
date: 2022-05-18
forum: General Help
---

### Post by nectarinebandit on 2022-05-18
On Ubuntu 20.04, the following worked successfully.


[LIST=1]
[*]Take a screenshot, which is stored to the clipboard
[*]Do a CTRL+P in a Word document on a VirtualBox Guest with Windows 7
[*]The image from the Ubuntu host's clipboard is pasted to the guest's word document
[/LIST]

On Ubuntu 22.04, steps #2 and #3 above no longer work.

**Does anyone know how the Ubuntu 22.04 screenshot utility is storing the a screenshot image to the clipboard? Does anyone know why screenshot images cannot be pasted to VirtualBox guests?** I suspect the screenshot tool is not storing images to a traditional clipboard. Whatever clipboard it is, the clipboard is inaccessible to VirtualBox guests.

The guest virtual machine with Windows 7 has the latest version of Guest Additions and the Bidirectional option is enabled for Shared Clipboard. This is working just fine since copying/pasting text back and forth works successfully.

The following scenarios do work.


[LIST=1]
[*]On Ubuntu 22.04, take a screenshot.
[*]Do a CTRL+P in a Libre Office document on the Ubuntu 22.04 host.
[*]The image is pasted successfully.
[/LIST]


[LIST=1]
[*]On the Windows 7 guest, take a screenshot using the snippet tool.
[*]CTRL+P the screenshot to a Libre Office document on the host
[*]The image is pasted successfully.
[/LIST]


[LIST=1]
[*]Copy text on either the host or guest virtual machine.
[*]CTRL+P on either host or guest.
[*]The text is successfully pasted.
[/LIST]

---

