---
title: "Kernel upgrade 2.6.24-17 help?"
date: 2008-05-26
forum: General Help
---

### Post by damis648 on 2008-05-26
Ok, please note I hold have the standard update sources enabled, as i know that previously the -17 kernel was only in the extra repositories that could be enabled. The new kernel just popped in my update manager, so i figured, ok they have fixed all issues and letting people upgrade. Well this is (kind-of) my fault, but while it was upgrading, i was typing a response to a thread on this forum. In the middle of this, a dialog popped up, which i only had a glimpse of which said "Please select your..." before it disappeared because i had hit the space bar, because i thought i was still typing. This is nothing major, but now when i boot up,  the -17 kernel is not in the grub. Any ideas? I assume i should be able to use the new kernel if it is installed, and i have been able to before i did a reinstall without enabling the extra update repos. I just want to use the new kernel. Should i try uninstalling it and then reinstall it?, because i am still using the -16 kernel as it is the only one available in the grub.

---

### Post by damis648 on 2008-05-26
bump??

---

### Post by lvlo on 2008-05-26
Just try to reinstall it.

---

### Post by damis648 on 2008-05-26
Thats what i was thinking but i am not sure if the configuration from that window that disapearred will stay, because i would like to re-select whatever option that was...

---

### Post by cwbar_1 on 2008-05-26
If you are using "start-up manager," the update process would have asked you if you wanted to use your configuration or the package manager's default menu.

---

### Post by damis648 on 2008-05-26
Nope, just tried reinstalling it and it did no good. The funny thing was though, was that in the terminal output of synaptic, it said "updating /boot/grub/menu.lst  done.". Any more ideas?

PS. I just checked my menu.lst, and the entry is not in there either... But i think i might know the problem, but i am not sure. A while ago, my computer would not boot because of an invalid UUID, so i changed all UUIDs in the menu.lst to /dev/sda2... maybe this is causing the problem? I am about to manually add the new kernel to the grub and see if I can boot it, because it is clearly installed, i can see it in /boot.

---

### Post by damis648 on 2008-05-26
> **cwbar_1 said:**
> If you are using "start-up manager," the update process would have asked you if you wanted to use your configuration or the package manager's default menu.

I am using startup-manager, you think this would have prevented it from being added to the grub and thats what that dialog was?

EDIT: I just checked the startup-manager preferences and i could not find anything relevant... i tried restoring the default settings but it did no good. I am about to add the new kernel to the list manually so i can at least check all modules and everything work correctly, because if not there is no point in this anyway.

---

### Post by damis648 on 2008-05-26
Okay, i just manually added the new kernel to Grub. I managed to boot it, but the restricted Nvidia driver did not work and it ended up in safe graphics mode. I would install the proprietary driver from Nvidia but i have had lots of issues with it in the past so i will not bother with it. I think i will just stick with the -16 kernel for now? What real motive do i have to upgrade to the -17 kernel?

---

### Post by Ameneon on 2008-06-02
Personally, I've reverted back to the .16 kernel, .17 causes inexplicable slowdowns every few seconds that are not present there when I run from the .16 kernel in the same environment. Unless I should happen to come across what is causing it (unlikely as I don't have the time to sit and TS it any more than I already have) I doubt I'll upgrade before next version should come out as .16 works perfectly well for me anyway..

---

