---
title: "Ubuntu 13.04 Raring Ringtail Grub Help"
date: 2013-06-30
forum: General Help
---

### Post by Techyte on 2013-06-30
I recently attempted an upgrade from 12.10 to 13.04 through the terminal. Halfway through it tried to install the font pack. I pressed enter repeatedly but nothing happened, so I exited the terminal and downloaded the 13.04 iso and wrote it to a disk (Had to reinstall the burning software due to the computer being half 12.10 & 13.04). I booted to the disk but it didn't detect the messed up ubuntu as an OS so I just installed it to another partition. I booted into 13.04 and it worked perfectly so I formatted the old ubuntu partition. The next time I booted it came up with grub rescue and I couldn't boot, I realised that the computer was using the old grub off the disk that I formatted. So I removed grub from the mbr. Then reinstalled using these commands:
```
sudo mount /dev/sda12 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sda

```
Now when I boot all I get is a magenta coloured blank screen.
Please help, thanks in advance.

---

### Post by oldfred on 2013-06-30
What video card/chip?

You may need nomodeset.
I have nVidia and on every ISO boot and first boot after install I have to use nomodeset until I get the nVidia proprietary drivers installed.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

