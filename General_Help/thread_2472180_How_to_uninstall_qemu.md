---
title: "How to uninstall qemu"
date: 2022-02-20
forum: General Help
---

### Post by GirishSharma on 2022-02-20
When I says dpkg -l | grep qemu, it do not returns any message but when I type q and press the tab twice, I gets many qemu- options.  I have removed qemu completely but I don't know how I am getting package names when I type q and press tab twice.

---

### Post by MAFoElffen on 2022-02-20
> **GirishSharma said:**
> When I says dpkg -l | grep qemu, it do not returns any message [COLOR=#ff0000]but when I type q and press the tab twice,[/COLOR] I gets many qemu- options.  I have removed qemu completely but I don't know how I am getting package names when I type q and press tab twice.

What do you mean by what is highlighted in red?

Could you please post the exact command you typed and what the results are within CODE TAGs?

And what command did you use to remove Qemu? Something like this?
```

sudo apt purge --auto-remove qemu
## OR
sudo apt purge --auto-remove qemu-system-x86

```

---

### Post by GirishSharma on 2022-02-20
> 
girish@girish-System-Product-Name:~$ sudo apt purge --auto-remove qemu
[sudo] password for girish: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'qemu' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
girish@girish-System-Product-Name:~$ sudo apt purge --auto-remove qemu-system-x86
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package 'qemu-system-x86' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
girish@girish-System-Product-Name:~$ q
qbittorrent               qemu-microblazeel         qemu-sh4                  qemu-system-mips64        qemu-system-xtensa
qemu-aarch64              qemu-mips                 qemu-sh4eb                qemu-system-mips64el      qemu-system-xtensaeb
qemu-aarch64_be           qemu-mips64               qemu-sparc                qemu-system-mipsel        qemu-x86_64
qemu-alpha                qemu-mips64el             qemu-sparc32plus          qemu-system-nios2         qemu-xtensa
qemu-arm                  qemu-mipsel               qemu-sparc64              qemu-system-or1k          qemu-xtensaeb
qemu-armeb                qemu-mipsn32              qemu-storage-daemon       qemu-system-ppc           qmqp-sink
qemu-cris                 qemu-mipsn32el            qemu-system-aarch64       qemu-system-ppc64         qmqp-source
qemu-edid                 qemu-nbd                  qemu-system-alpha         qemu-system-riscv32       qpdf
qemu-ga                   qemu-nios2                qemu-system-arm           qemu-system-riscv64       qpdldecode
qemu-hexagon              qemu-or1k                 qemu-system-avr           qemu-system-rx            qrttoppm
qemu-hppa                 qemu-ppc                  qemu-system-cris          qemu-system-s390x         qshape
qemu-i386                 qemu-ppc64                qemu-system-hppa          qemu-system-sh4           qt-faststart
qemu-img                  qemu-ppc64le              qemu-system-i386          qemu-system-sh4eb         quirks-handler
qemu-io                   qemu-pr-helper            qemu-system-m68k          qemu-system-sparc         quote
qemu-keymap               qemu-riscv32              qemu-system-microblaze    qemu-system-sparc64       quote_readline
qemu-m68k                 qemu-riscv64              qemu-system-microblazeel  qemu-system-tricore       qvlc
qemu-microblaze           qemu-s390x                qemu-system-mips          qemu-system-x86_64        
girish@girish-System-Product-Name:~$ q


When there is no qemu package installed, then from where and how I am getting above qemu* packages when I type q and press the tab key twice in the terminal.

---

