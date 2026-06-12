---
title: "Changing grup default and removing kernel option from list?"
date: 2023-11-27
forum: General Help
---

### Post by grandkodiak2 on 2023-11-27
I haven't used linux in awhile but it's a dual boot with windows 11. last time I updated the kernel, it stopped being able to boot in (except for windows)... unless you scrolled down to the older kernel. 

1. How can I remove the non functioning kernel from the list? (assuming i can also delete the physical file associated with it too, or is there a cleaner/better way?)

2. How can I change the default to land on windows? everytime I have an unexpected forced reboot or power failure my system either dead ends at the bad kernel and sits or when it still worked, at the gui loggin prompt. 

Thank you!

---

### Post by deadflowr on 2023-11-27
> 1. How can I remove the non functioning kernel from the list? (assuming i can also delete the physical file associated with it too, or is there a cleaner/better way?)
```
sudo apt purge linux-image-*number-of-kernel-version-here*-generic
sudo apt autoremove --purge
```
replace *number-of-kernel-version-here* with the actual listed kernel number.

example would look something like linux-image-5.15.0-120-generic

> 2. How can I change the default to land on windows? everytime I have an unexpected forced reboot or power failure my system either dead ends at the bad kernel and sits or when it still worked, at the gui loggin prompt.

lot of ways but I find setting custom grub the easiest to manipulate and deal with
See: [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")
I would think that you'd just have to place the windows entry higher in the custom file.

---

