---
title: "Laptop usually won't stay suspended"
date: 2014-09-02
forum: General Help
---

### Post by peel on 2014-09-02
Hi all,
I'm using a HP ENVY 17T that is only a month or so old, running Xubuntu 14.04. My computer is able to suspend no problem, but in general will eventually turn back on without me opening the lid or pushing any buttons. Often I get the feeling that it has happened because I moved it (it seems like it's more likely to happen when I pick it up or something), but it also sometimes happens while lying perfectly still.

I've done some reading on similar problems with other machines. I saw that in many cases it has to do with USB 3.0, and I saw that people recommended to edit /etc/pm/config.d/unload_module, but I don't appear to have such a file. Perhaps this file only existed on older versions of Ubuntu. I tried to create such a file and write SUSPEND_MODULES="xhci-hcd" in it as people recommended to add that to the file, but that didn't work so I deleted the file. Someone wrote that on their chromebook they found out that their trackpad activating was causing this problem, but I tried moving my finger on the trackpad while the computer was suspended and that didn't wake the computer up so I doubt that's the problem. Many people also recommended looking at pm-suspend.log under var/log, and I did that, but I don't really understand what I can learn from it exactly, and how the displayed information would apply to the problem. Perhaps I'm not an advanced enough Linux user yet.

In any case, if anyone has any ideas, or would be able to help me diagnose the issue or offer any help whatsoever, I would be very grateful. Thank you.

---

### Post by Toz on 2014-09-04
Which wakeup events are enabled in your system?
```
cat /proc/acpi/wakeup
```

---

