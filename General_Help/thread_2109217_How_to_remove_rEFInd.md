---
title: "How to remove rEFInd"
date: 2013-01-26
forum: General Help
---

### Post by Von Kuser on 2013-01-26
Hello everyone!

I am a new to Ubuntu (I started to use it a week ago) and also I am not too familiar with EFI UEFI, I have read a little, but I am still not sure of what it is. I have a Macbook 8,2 and managed to install Windows 8 an Ubuntu 12.10 along with Mac OSX, to make my life 'easier' I decided to install 'rEFInd' which technically would allow me to select which operating system to load upon turning my laptop on.

Now I get this:
[IMG]http://i.imgur.com/pkD2kfq.png[/IMG]

Four of the options with Tux do not work. Both the only one that works Tux and the Windows one take me to a second menu to select to boot from Ubuntu or Windows 8. Which makes completely pointless having rEFInd, and slightly more annoying.I would rather remove rEFInd and simply boot Ubuntu/Windows using the bootloader provided by Ubuntu.

I alredy tried removing the refind folder from my EFI folder in MacOSX (**"\EFI\refind\refind.efi"**)

I also tried doing [THIS]("https://bbs.archlinux.org/viewtopic.php?id=152832") using the Terminal in Ubuntu. 

but when I do **"# efibootmgr -v"** I get the following message:

```
Fatal:  Couldn't open either sysfs or procfs directories for accessing EFI variables.
Try 'modprobe efivars' as root.
```

I tried running **'modprobe efivars'** in  the terminal But it makes no difference. So what could I do to remove rEFInd? (Any OS)

Thank you,
-Von Kuser

---

