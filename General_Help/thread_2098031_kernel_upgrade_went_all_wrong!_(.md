---
title: "kernel upgrade went all wrong! :("
date: 2012-12-25
forum: General Help
---

### Post by tubunu on 2012-12-25
Hello,
I've recently upgraded my kernel, and removed the old one so I have no way of choosing the old one that worked. What can I do now that I only see a black screen after booting? I appreciate any input, thank you in advance.

---

### Post by dino99 on 2012-12-25
you might have learnt your lesson now ):P

try recovery boot mode (hold "shift" key down at bios end process to get the grub menu) then select repair.

---

### Post by tubunu on 2012-12-25
I cannot see the "repair" option.. Holding SHIFT down doesn't do anything. I can see grub menu without holding down SHIFT. What else can I try?

EDIT: 
OK, do you mean getting to Recovery Menu and selecting dpkg - repair broken packages? It doesn't seem to fix anything, I still get a black screen. Could it be that my **display drivers** are wrong? When I select "root - drop to root shell prompt" in recovery mode and run: startx, the system boots to a root account, but the display seems funny, looks a bit odd, like it has a wrong resolution.

---

### Post by raja.genupula on 2012-12-25
try with <kbd>Esc</kbd> key .

---

### Post by snowpine on 2012-12-25
> **tubunu said:**
> I cannot see the "repair" option.. Holding SHIFT down doesn't do anything. I can see grub menu without holding down SHIFT. What else can I try?

EDIT: 
OK, do you mean getting to Recovery Menu and selecting dpkg - repair broken packages? It doesn't seem to fix anything, I still get a black screen. Could it be that my **display drivers** are wrong? When I select "root - drop to root shell prompt" in recovery mode and run: startx, the system boots to a root account, but the display seems funny, looks a bit odd, like it has a wrong resolution.

If you can successfully boot to a root prompt, then you can install the old kernel that you removed, and then boot to it using GRUB. :)

---

