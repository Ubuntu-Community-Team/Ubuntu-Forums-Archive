---
title: "No default or ui configuration directive found when booting from Live Ubuntu USB"
date: 2014-01-25
forum: General Help
---

### Post by Hishighness on 2014-01-25
Hey all, I've been trying to set up a live USB stick so I can use an old computer who's hard drive I want to format and use elsewhere, but every time I create it and try to boot I get this.

```
ERROR: No configuration file found
No DEFAULT or UI configuration directive found!
boot: _
```

I've tried using 3 different ISOs but get the same thing, I've also tried 3 different USB creation programs (unetbootin in Ubuntu, the Startup Disk Creator included in Ubuntu, and the Universal USB Installer on Windows 7) in case that was the problem, same thing.

I've also searched google and tried the renaming the isolinux folder, .bin and .cfg to syslinux but still get the same error message.

My computer boots fine from the Ubuntu 12.10 CD I have (which is what I'm using to type this and also one of the ISOs I used)

I'm out of ideas, I'm wondering if anyone else has something I could try.

Thanks for your time,
H420

---

### Post by Hishighness on 2014-01-26
It's a 16gb usb stick, is there a size limit?

---

### Post by ros3 on 2014-02-25
have same problem when i trying to boot from usb 12.04 64bit. tried to change filenames and different format on usb..

---

### Post by ciberzonaaljarafe on 2014-09-15
Format the pendrive in FAT16, some older motherboards do not recognize the FAT32, this resolved my problem with my old Asrock K7VT4A pro

---

