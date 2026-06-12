---
title: "Boot issue. Please help."
date: 2018-03-01
forum: General Help
---

### Post by nateman595 on 2018-03-01
I have used Ubuntu for the last few years and have no encountered many issues. But I got a new pc and switched from windows 10 to Ubuntu. The installation went as normal. First boot up was normal. I then installed some updates, no other apps or such. I then had to restart to finish the update.

 When doing so I got a black screen saying acpi lookup failure and mods ignore couldn't get uefi dB list.

I then went to recovery mode and selected update grub and then selected resume boot and that worked. After that I turned the pc off and back on and got stuck at the grub/purple screen and it will only boot into os after selecting update grub.

So the help I need is to some how make update grub permanent so I don't have to go to recovery every time.

---

### Post by cruzer001 on 2018-03-01
Hello

Please post the output of:
```
lsb_release -a && uname -r && echo $XDG_SESSION_TYPE
```
First try nomodeset for one session:
[https://ubuntuforums.org/showthread.php?t=1613132](https://ubuntuforums.org/showthread.php?t=1613132)

And there is boot-repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

You removed Windows and installed Ubuntu or is this dual boot using UEFI?

---

