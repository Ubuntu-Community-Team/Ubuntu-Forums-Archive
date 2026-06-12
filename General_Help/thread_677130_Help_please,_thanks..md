---
title: "Help please, thanks."
date: 2008-01-24
forum: General Help
---

### Post by prelan on 2008-01-24
i got a new sony VAIo laptop, i installed ubuntu, realised i dont want to learn a computer language... uninstalled it... got error 22 grub loading. i then re-installed it to be able to boot into windows and thats all good but the ubuntu partition is taking up all the free space and vista can't even perform stupid tasks cuz theres no room for scracth files. i want GRUB off of my laptop and ubuntu untill i feel i'm ready to learn that stuff. thanks guys =) 

Steve

---

### Post by LaRoza on 2008-01-24
What computer language?

Well, you need to reinstall the Windows bootloader. Use the Windows install disk, or the Super Grub Disk.

With the SGD, it is under "Advanced->Windows (Advanced)" and is the first option. Just download it, boot from it. 

Should take a second or two (literally) then reboot. Windows should boot. In Windows, use Computer Management->Disk Management to delete the Linux partitions, then extend the Windows partition to fill the space.

See the link in my sig for the SGD.

---

### Post by Bruce M. on 2008-01-24
> **prelan said:**
> i got a new sony VAIo laptop, i installed ubuntu, realised i dont want to learn a computer language... uninstalled it... got error 22 grub loading. i then re-installed it to be able to boot into windows and thats all good but the ubuntu partition is taking up all the free space and vista can't even perform stupid tasks cuz theres no room for scracth files. i want GRUB off of my laptop and ubuntu untill i feel i'm ready to learn that stuff. thanks guys =) 

Steve

Sorry to see you leaving.  Ubuntu is a great OS!

That said, you need to run "fixmbr" ... when windows starts to boot go to recovery mode (r - I think) and type:

```
FIXMBR
```

That kills any bootloader you installed.

Hope this helps.

---

