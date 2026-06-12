---
title: "Upgraded to Ubuntu 13.04, now Windows 7 won't boot"
date: 2013-07-07
forum: General Help
---

### Post by BlackL1ght on 2013-07-07
After upgrading to Ubuntu 13.04, my windows boot option now says something like invalid efi (I'll reboot and edit this to put the exact message if necessary. I've tried using bootfix from a dvd, but it gave an error, which I can also post if necessary. What are my options from here?

---

### Post by DJ_Max on 2013-07-07
I would read here if you haven't already [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

What is your setup? How many HDD's, where is windows? Logs would help a tremendous amount.

---

### Post by BlackL1ght on 2013-07-07
Just one HDD, in an Asus U5A7 laptop. If you can tell me what logs you need, I'll post them here. I was running Ubuntu 12.10 before and had no problems dual-booting through what I think is called GRUB.

When I choose the option for Windows 7, it says ```
error: invalid efi path
```

---

### Post by BlackL1ght on 2013-07-09
What information do you need in order to help me?

---

### Post by fantab on 2013-07-09
How did you upgrade? Was this an internal Upgrade from Update-Manager? Or did you replace 12.10 with 13.04 doing clean install from 13.04 DVD/USB?

Was your windows7 booting in UEFI?

**[BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair")** utitility can fix most of the boot problems. Boot-Repair also generates a 'BootInfo Summary', post the link to your BootInfo Summary, Lets see what is going on.

---

