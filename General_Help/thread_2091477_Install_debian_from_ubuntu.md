---
title: "Install debian from ubuntu"
date: 2012-12-05
forum: General Help
---

### Post by Atomic_kemo on 2012-12-05
I read an article that explained how to make a menu-entry for another linux in grub and boot to install without burning any CDs.
The problem is the article is old and I have Ubuntu 12.10 with GRUB2 so I can't make the entry and I don't understand how to.
Please give me detailed instructions, I have the Linux ISO (Debian).

---

### Post by coffeecat on 2012-12-05
If you mean adding an entry to grub2 so that you can boot from an ISO, here are some links for you.

Tutorials and Tips thread (not up-to-date):

[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

Community Documentation for booting Ubuntu ISO:

[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

Community Documentation for booting ISOs of some other distros:

[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

There is nothing specifically about Debian in the two documentation pages but there should be enough information for you to create a grub entry.

---

### Post by Atomic_kemo on 2012-12-05
Thanks it worked and booted, but after selecting language and keyboard layout it asks for CD to be inserted in CD-ROM

this is my menu-entry

```
menuentry "Debian" {
loopback loop /boot/iso/debian-6.iso
linux (loop)/install.386/vmlinuz boot=live iso-scan/filename=/boot/iso/debian-6.iso noeject noprompt --
initrd (loop)/install.386/initrd.gz
}
```

---

### Post by houseworkshy on 2012-12-05
There is also advice here [http://www.debian.org/releases/stable/amd64/apas02.html.en#howto-getting-images-hard-disk](http://www.debian.org/releases/stable/amd64/apas02.html.en#howto-getting-images-hard-disk)  It's in the section A.2.4 bit which links to more details on the bootloaders here [http://www.debian.org/releases/stable/amd64/ch05s01.html.en#boot-initrd](http://www.debian.org/releases/stable/amd64/ch05s01.html.en#boot-initrd)
Well that's for AMD 64, there is similar advice for other architectures too.

---

