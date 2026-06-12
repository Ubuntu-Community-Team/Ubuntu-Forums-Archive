---
title: "How to set Kernel Parameters for Ubuntu 24.04.1 with TPM-backed FDE ?"
date: 2024-10-26
forum: General Help
---

### Post by nquireery1100 on 2024-10-26
[COLOR=#000000]I’m currently exploring the new experimental feature of TPM-backed Full Disk Encryption (FDE) on Ubuntu 24.04.1 on a Thinkpad and would like some guidance on setting kernel parameters for my system.[/COLOR]
[COLOR=#000000]From my understanding, this version utilizes UKI (Unified Kernel Image) and is managed via Snap, which is a bit different from the traditional approach of modifying GRUB.[/COLOR]
[COLOR=#000000]Could anyone provide insights on:[/COLOR]


[LIST=1]
[*]**How to set kernel parameters for a UKI-based system?** Are there specific files or commands I need to use?
[*]**Any recommendations for kernel parameters that might be beneficial for optimizing TPM-backed FDE?**
[*]**Potential pitfalls or considerations I should be aware of when implementing this feature?**
[/LIST]

[COLOR=#000000]Thank you for your help![/COLOR]

[COLOR=#000000]note i have searched the internet far and wide and have found nothing ! any help would be greatly appriciated !! [/COLOR]:grin:

---

### Post by omid_1985 on 2024-12-04
I guess it would be similar to Ubuntu Core:
[https://ubuntu.com/core/docs/modify-kernel-options](https://ubuntu.com/core/docs/modify-kernel-options)


I have yet to dig into it too much, though. I checked it to get hibernation working on FW13 Ultra Core, but It was too much of a task for something still experimental on 24.04.1, and when I wondered if it would stick around for the next LTS release.

---

