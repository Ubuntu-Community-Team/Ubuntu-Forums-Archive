---
title: "Check forced at boot, freezes"
date: 2008-02-22
forum: General Help
---

### Post by zackf on 2008-02-22
Today when I tried to boot Ubuntu I get ```
/dev/sda4 has been mounted 25 times without being checked, check forced.
```
And it freezes every time at 36.2%. I have seen how to disable this in fstab, but obviously I can't get that far. Is there somethign I can pass at the grub menu that will stop this?

Thanks.

---

### Post by pointone on 2008-02-22
Firstly, make sure it's actually frozen. How long have you waited for it to continue? If fsck is checking a large file (CD images, virtual drives, etc.) the progress bar/percentage won't increase until it completes scanning the file. When fscking my one storage drive, it sometimes pauses for two or three minutes at a time.

---

### Post by zackf on 2008-02-23
Thank you for your response.

I let it sit for about an hour and it hadn't made any progress, then I remember some arguments to pass to grub when I had problems with an install freezing with fedora. I added 'noapic nolapic apci=off' and it scanned everything in about 4 minutes and now (obviously) I'm back on.

Rock on.

---

