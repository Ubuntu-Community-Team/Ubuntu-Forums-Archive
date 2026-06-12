---
title: "special characters in mounted drive"
date: 2008-05-03
forum: General Help
---

### Post by vaskark on 2008-05-03
I have a partition that holds all my stuff (pics, music, videos, etc) and i configured it to mount whenever i reboot my system (using fstab). However, some of my music filenames have special characters that aren't being rendered properly - like in Sigur Rós**. **So how can I get my system to recognize these characters? Here is the line for the mounted drive from fstab:

*/dev/sda4 /media/winD vfat user,auto,fmask=0111,dmask=0000 0 0*

Any help is appreciated.
Thanks.

---

### Post by vaskark on 2008-06-26
*bump*

---

### Post by VMC on 2008-06-26
> **vaskark said:**
> I have a partition that holds all my stuff (pics, music, videos, etc) and i configured it to mount whenever i reboot my system (using fstab). However, some of my music filenames have special characters that aren't being rendered properly - like in Sigur Rós**. **So how can I get my system to recognize these characters? Here is the line for the mounted drive from fstab:

*/dev/sda4 /media/winD vfat user,auto,fmask=0111,dmask=0000 0 0*

Any help is appreciated.
Thanks.

What exactly do yo want to do with those files? Copy them or play the music?

You can use a "greedy" character copy if that would help. Providing you want to move or copy the files.

---

### Post by mcduck on 2008-06-26
Add "iocharset=utf8" to the mount options (use whatever character set your partition is actually using).

```
/dev/sda4 /media/winD vfat user,auto,iocharset=utf8,fmask=0111,dmask=0000 0 0
```

---

