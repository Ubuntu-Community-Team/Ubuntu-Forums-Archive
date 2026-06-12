---
title: "How do I dump Ubuntu?"
date: 2014-12-17
forum: General Help
---

### Post by Shooter1938 on 2014-12-17
Hi.  I installed Ubuntu expecting to be able to remove it if I wasn't satisfied.  I am 76 years old and find it a bit too difficult for me and would like to remove Ubuntu completely.  I use Windows 7 and Ubuntu does not show on my  'add/delete programmes', and I am fed up with having to use the Ubuntu page first to swap back to 7. It's as if Ubuntu wants to take control completely and make things difficult. Can anyone help please?

---

### Post by Bucky Ball on 2014-12-17
It sounds like you installed Wubi rather than Ubuntu to a separate partition. Is this the case? Wubi hasn't been supported for some time (although it is still available) so not many of us know much about it.

If you have installed Wubi, perhaps [THIS]("https://wiki.ubuntu.com/WubiGuide#Uninstallation") will be of some help, though. It is a guide to manually uninstalling Wubi from Win7.

---

### Post by mörgæs on 2014-12-17
How is Ubuntu difficult? Maybe we can help with that.

---

### Post by yancek on 2014-12-17
You will need to clarify first whether you installed Ubuntu using wubi or have it on a separate partition.  If you don't see it in the add/remove programs it may be on its own partition and you are likely using its bootloader to boot both windows 7 and Ubuntu.  If that is the case, you would need to put windows code in the master boot record and verify that it boots windows before formatting the Ubuntu partition.  You will likely need to use your windows 7 installation medium for that.

---

### Post by sgage on 2014-12-17
> **yancek said:**
> You will need to clarify first whether you installed Ubuntu using wubi or have it on a separate partition.  If you don't see it in the add/remove programs it may be on its own partition and you are likely using its bootloader to boot both windows 7 and Ubuntu.  If that is the case, you would need to put windows code in the master boot record and verify that it boots windows before formatting the Ubuntu partition.  You will likely need to use your windows 7 installation medium for that.

Or, you could use EasyBCD from Windows if you don't have Windows 7 installation media handy... I have been dual-booting Windows and Linux for years, and EasyBCD is my go-to tool in all sorts of situations.

---

### Post by egeezer on 2014-12-17
Here's a suggestion from someone even older than you are (I'm 81): keep your Ubuntu installation, but put an Xfce desktop on it - that works much more like W7 than Ubuntu does, and you will find it easy to get used to. I agree that the Unity desktop of plain Ubuntu is a big mess!

If you do want to switch to the Xfce desktop, let us know and we can give you a very simple way to do it.

---

