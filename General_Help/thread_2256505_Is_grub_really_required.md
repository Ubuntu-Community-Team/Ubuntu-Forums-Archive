---
title: "Is grub really required?"
date: 2014-12-13
forum: General Help
---

### Post by Ulf_Dunkel on 2014-12-13
On several Ubuntu clients which I maintain, the users complain that they still see the violet Grub screen from time to time, depending on whether the machine has got a system upgrade or has experienced a crash before.

In /etc/default/grub, I use these settings:

[INDENT]GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable generation of recovery mode menu entries
GRUB_DISABLE_RECOVERY=true
[/INDENT]

But I wonder if grub is really required at all when I will never want to boot or select any other than the latest currently installed version of Ubuntu?

---

### Post by sudodus on 2014-12-13
Grub is a bootloader. You need a bootloader, but could use another one, if you don't like grub. Maybe you mean 'Is the grub ***menu*** really required?'. The answer to that question is that it can be switched off. But some error conditions (maybe caused by events like those you describe) can re-activate the grub menu.

You can find descriptions of the details browsing the internet, for example the following link and links from it

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

