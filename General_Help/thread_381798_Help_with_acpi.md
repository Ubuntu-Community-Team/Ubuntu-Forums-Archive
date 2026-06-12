---
title: "Help with acpi"
date: 2007-03-11
forum: General Help
---

### Post by 67GTA on 2007-03-11
I have had sucsess setting everything up except for ATI driver. Installed with Envy, works now. The only hurdle left is the cpu and ati fans. They run too fast and never stop. I tried lm-sensors to see what the specs were, but my board does not support it. I went to /proc/acpi/fan to see if I could tweak some settings, and all the files under /acpi are empty, there are no configuration scripts written. What is controlling my fans? Where do I look for a solution?

---

### Post by 67GTA on 2007-03-11
Well I ran acpi --help in terminal and it showed no option for fan and --thermal is not supported. Is there a dependency I need for thermal support, or is it just my board? I assume since thermal is not supported then it can't tell the fans to start or stop at the thermal limits. If I turn off, or uninstall acpi will my board regulate itself?

---

