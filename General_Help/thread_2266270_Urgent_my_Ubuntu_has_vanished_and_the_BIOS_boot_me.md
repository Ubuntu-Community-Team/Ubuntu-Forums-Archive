---
title: "Urgent: my Ubuntu has vanished and the BIOS boot menu has disappeared!"
date: 2015-02-21
forum: General Help
---

### Post by Bobby_James on 2015-02-21
Something has gone horribly wrong with my 12.04 system.

I let the battery die and the machine rebooted. I was surprised that it went into Windows 8 as the boot menu is setup for Ubuntu.

I exited Windows, pressed F2 and went into the boot menu. I can't remember exactly what it used to look like but the ability to have boot settings has vanished! I used to be able to select between UEFI and CSM (I think). Now that option no longer exists. I can only boot into Windows.

Also, the clock went back to January 15 2015 at an incorrect time.

I have no idea what has happened. Could it be a rootkit? Would that alter the BIOS menu? I am using a Samsung Ultrabook.

The attached show what Disk Management sees in Windows 8.

What can I do to get back into Ubuntu? Thanks!

---

### Post by Bobby_James on 2015-02-21
I managed to solve the problem. What had happened is that, in the boot menu, the "Secure Boot" was "Enabled". By disabling this, I saw the menu that allowed UEFI, etc.

Does anyone have any opinions as to why the boot menu changed from Secure Boot Disabled to Enabled and why the clock changed at the BIOS level?

Thank you.

---

