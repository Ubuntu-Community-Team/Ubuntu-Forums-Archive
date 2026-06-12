---
title: "[SOLVED] System hangs on startup"
date: 2007-12-21
forum: General Help
---

### Post by elicoten on 2007-12-21
Hi

For some reason the system won't startup. I've tried recovery mode and it just hands, the last line on the screen is "setting up console font & keymap" (or something similar). How do I go about troubleshooting this? I'm using either Ubuntu 6.06 or 6.10.

Thanks in advance

---

### Post by cdenley on 2007-12-21
Does a livecd boot? If it does, then check your hard drive.

```

sudo cat /dev/sda>/dev/null

```

This will take a long time. Replace /dev/sda with the path to your disk. If you have multiple disks, identify it using the output from "sudo fdisk -l". If the drive is bad, it will give an error. If the drive isn't bad, it will finish with no output.

If the hard drive isn't bad, and an ubuntu livecd works, then it must be a software issue, and should be fixed by a reinstall. If the livecd doesn't work, then try a livecd for a different distribution. If you can't get any distribution to boot and run properly, then it's probably a hardware problem.

---

### Post by elicoten on 2007-12-22
The hard drive was fine so I'm just going to re-install from the latest Ubuntu 7.10 CD.

Thanks

---

