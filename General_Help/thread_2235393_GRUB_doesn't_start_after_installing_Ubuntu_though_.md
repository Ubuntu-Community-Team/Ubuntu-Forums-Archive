---
title: "GRUB doesn't start after installing Ubuntu though GRUB is installed"
date: 2014-07-20
forum: General Help
---

### Post by Electronblue on 2014-07-20
After successfully installing Ubuntu 14.04 on my 64 bit notebook (UEFI enabled), I tried to boot it. The first time it worked (GRUB showed up and let me choose between Ubuntu and Windows 8.1) and Ubuntu works too. The second time I started my notebook, GRUB did not show up anymore. Instead, Windows was booted immediately. I figured that it must have to do with the boot order configured in the UEFI, so I went into the UEFI and set ubuntu (of which there were two entries for some reason) above the Windows Boot Manager. I thought that may fix the problem and indeed, the next time I started the computer, GRUB started as well and I could boot into Ubuntu. However, after starting it again for the third time, GRUB again does NOT show up (i.e. Windows starts again) even though Ubuntu is still on top of the booting list in the UEFI. Could anybody help me to fix this problem so that I can launch my newly installed Ubuntu via GRUB?

---

### Post by slooksterpsv on 2014-07-20
Download my app - efibootorder in my sig - and try changing the order that way. You can also paste the output of:
```

sudo efibootmgr

```
Which will tell us what is really set to boot first.

UEFI/EFI isn't uniform so some implementations are radically different. You can sometimes change the default boot in BIOS, some apps like my app and efibootmgr will save the changes and keep them, sometimes it won't.

Make a recovery dvd/USB drive just in case. Toshiba uses like an eRecovery software (mine required a 16GB flash drive!). Others have a way of creating the medium.

Here's a few q?:
1) What is the make/model of the computer (Asus, Lenovo, Toshiba, etc.)?
2) Do you want just GRUB only and no UEFI? If so you'll that's a whole process overall.

Try my app first.

---

### Post by Electronblue on 2014-07-21
Thanks for your reply. I tried your tool efibootorder as well as  efibootmgr on an Ubuntu Live disc. In efibootorder, I saw three "ubuntu"  boot options, my DVD drive and the Windows Boot Manager. So I put the  three ubuntu boot options at the top of the list, saved the config and  rebooted. Still, just Windows booted and no GRUB showed up at all. Then I  checked the boot order in the UEFI and saw that suddenly ALL ubuntu  partitions had disappeared, only the Windows Boot Manager was left.
So  I went back into the Ubuntu live disc and tried your tool again,  however it also didn't show "ubuntu" as a boot option anymore (neither  did efibootmgr). So I guess Windows has now entirely deleted the Ubuntu  bootloader. -_-
I also tried installing boot-repair, however it seems that it does not work on my computer because of the architecture:
[I]
W:  Failed to fetch  [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)   404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/I]


Also, here is a screenshot of what efibootmgr and efibootorder say:

[http://i.imgur.com/Dy6ommr.png](http://i.imgur.com/Dy6ommr.png)


My PC is an MSI Gp60 2PE with an Intel Core i7 4710, 8GB RAM and an Intel HD 4600 GPU.

Help :(

---

### Post by slooksterpsv on 2014-07-22
We can try to manually create the entry with efibootmgr, via:
sudo efibootmgr -c -L Ubuntu

---

