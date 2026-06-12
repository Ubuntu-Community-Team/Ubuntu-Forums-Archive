---
title: "No keyboard detected"
date: 2020-10-29
forum: General Help
---

### Post by satimis on 2020-10-29
Hi all,

Ubuntu 20.04 Desktop

I have been playing around on BIOS in order to make the Win10 USB boot drive, burned on its ISO, to install Win10 on a physical drive without a solution.

According to my recollection my last attempt was on BIOS Advanced Tab, changing USB3.0 to USB2.0. Now on booting I can't enter BIOS mode on pressing DEL/F2, complaining "No Keyboard Detected".

However the PC boots straight to Ubuntu desktop.  The keyboard is then working.  It is quite funny to me.

Please advise how can I enter BIOS mode at booting.  Thanks

---

### Post by CelticWarrior on 2020-10-29
If this is a desktop computer you may need to reset the firmware which should be UEFI, not BIOS, unless it's an old machine.

---

### Post by satimis on 2020-10-29
> **CelticWarrior said:**
> If this is a desktop computer you may need to reset the firmware which should be UEFI, not BIOS, unless it's an old machine.
Hi,

This is a desktop computer having been running several years.  It has UEFI.

Please advise how to reset the firmware?  Thanks

Regards

---

### Post by CelticWarrior on 2020-10-29
Please check the motherboard's manual.

It's usually done by shortening a jumper.

---

### Post by ActionParsnip on 2020-10-29
Have you tried a different USB port....like the front USB so its a different root hub

---

### Post by satimis on 2020-10-29
> **CelticWarrior said:**
> Please check the motherboard's manual.

It's usually done by shortening a jumper.
Hi,

$ hardinfo```

.......
M5A97 LE R2.0 (ASUSTeK Computer Inc.)
....

```

I'll search its manual on Internet and come back later.  Under which item shall I check?  Thanks

Regards

---

### Post by satimis on 2020-10-29
> **ActionParsnip said:**
> Have you tried a different USB port....like the front USB so its a different root hub
Hi,

I ran Win10 USB boot disk on the front USB port

Regards

---

### Post by tea for one on 2020-10-29
> **satimis said:**
> However the PC boots straight to Ubuntu desktop.  The keyboard is then working.  It is quite funny to me.

As you can boot into Ubuntu, you can reach the UEFI set up screens with this command
```
sudo systemctl reboot --firmware-setup

```

Hopefully, you can then set your UEFI to default (or factory) and then your keyboard will be recognised as before.

---

### Post by satimis on 2020-10-30
Hi all,

Lot of thanks for your advice and time spent.

Problem solved as follow;

1) Plugin the receiver of wireless Keyboard and mouse in the USB port at the front of the PC box
2) Started PC and pressed DEL.  This time it worked entering the BIOS setup page.
3) Selected Advanced Mode
4) Advanced -> Legacy USB Configuration -> USB 3.0 Support -> select Enabled
5) Exit -> Save Changes & Reset -> Yes

Turned off PC and replugin the receiver in the USB port at back of the PC box
Restarted PC.  This time - Keyboard detected

I think the USB port at front of the PC is USB 2.0

Regards

---

