---
title: "Grub Rescue"
date: 2013-06-12
forum: General Help
---

### Post by bedekelly on 2013-06-12
Hi all,

After using gParted to delete a linux mint partition and expand my ubuntu partition into the unallocated space, on boot I get a "grub rescue" prompt. Any help appreciated, since I don't have a clue what commands this prompt will respond to. Will it be possible to re-instate the regular grub?

Thanks for your time.

---

### Post by zero2xiii on 2013-06-12
Hay,

Please see my thread ["Help Us Help You]("http://ubuntuforums.org/showthread.php?t=2140012")" for some help, also my signature...

Cheers

---

### Post by grahammechanical on 2013-06-12
When we install Ubuntu as part of the installation process Grub is installed into the MBR of the hard disk. If we then install Linux Mint it will put Grub into the MBR of the hard disk over writing what was put there by Ubuntu. If we then delete Linux Mint as you have done then when Grub in the MBR starts to work it cannot find its configuration files on the Linux Mint partition and it stops working and cries "Rescue me!" Grub is broken and needs to be re-installed.

The way to avoid this issue is to boot into Ubuntu and run

```
sudo grub-install /dev/sda
```

That will put Ubuntu back in control of Grub in the MBR and we will still be able to boot into Ubuntu once Linux Mint has been removed. Then we run

```
sudo update-grub
```

and that reconfigures the Grub boot menu and removes the listing of Linux Mint.

You need this

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The same developer has also produced OS-Uninstaller. To late for you but not for others to avoid this problem.

[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

Regards.

---

### Post by bedekelly on 2013-06-12
Thanks to both of you. I booted to a live CD of 12.04 and then installed and ran boot-repair. It seems stuck on the "Scanning systems" dialogue - am I simply being too impatient, or could there be some other factor affecting boot-repair?

---

### Post by bedekelly on 2013-06-12
Great, problem solved - I used the Terminal method from this article on a live cd. Thanks for the support, and putting up with my newbieness! :')[URL="http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/"]

http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot[/URL]/

---

