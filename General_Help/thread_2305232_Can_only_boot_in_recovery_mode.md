---
title: "Can only boot in recovery mode"
date: 2015-12-03
forum: General Help
---

### Post by The GNUbie on 2015-12-03
I have formatted my HD and completed reinstalled many different versions, each have the same problem, none will boot directly into the GUI.    It gets to the Xubuntu splash screen, then the pixels get distorted (lines, etc) and the system hangs.   If I go into GRUB, select recovery mode and immediately select resume, everything works just fine.

This is more of a nuisance than anything and Im trying to restore an old Dell Mini9 for fun so there is no rush.  I have tried looking in the boot.log and dmesg but couldnt find anything.   

If you have any suggestions on what I can try next or where else I should look, it would be appreciated.

Thank you,
Ryan

---

### Post by grahammechanical on 2015-12-03
Here are some things to consider.

1) The Live session uses an open source video driver.
2) Recovery mode>Resume uses an open source video driver
3) When we install and tick the box "Install third party software" we get a proprietary video driver.
4) Newer proprietary video drivers no longer support older video adapters.

Try using the Additional Drivers utility to either use the open source video driver or a legacy proprietary video driver if there is one on offer. Or, if we are installing, do not tick the box "Install third party software." Then once we get to a working desktop we can install the proprietary video driver if we want to and also the third party audio & video codecs by installing Ubuntu Restricted Extras.

Regards.

---

