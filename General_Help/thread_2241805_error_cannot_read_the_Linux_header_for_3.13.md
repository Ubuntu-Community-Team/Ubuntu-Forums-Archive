---
title: "error: cannot read the Linux header for 3.13?"
date: 2014-08-28
forum: General Help
---

### Post by axehind007 on 2014-08-28
Hi all,

I have a bunch of servers running Ubuntu 12.04 with the latest updates installed. I just updated the kernel on them all to the trusty 3.13
kernel and all went well except with one machine. The machine displays the error

error: cannot read the Linux header
error: you need to load the kernel first


I can press a key and it will bring me to the grub boot menu and will let me boot using the 3.11 kernel. I've
tried various things like running update-grub and uninstalling 3.13 and reinstalling it but it doesnt seem to work. Any ideas on what else I can try?

Thanks!

---

### Post by Bashing-om on 2014-08-30
axehind007; Hi !

As this is a production server, can not spend a lot of time trouble shooting and looking for a solution.
How about a shotgun approach and just purge/(RE-)install grub ?
```

sudo apt-get remove --purge grub grub-pc grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sda

``` in this case where there is no separate /boot partition, and the operating system is installed onto the 1st hard drive AND booting is via MBR.
Adjust 'sda' as required !! Booting EFI will be a different routine !
In the reconfigure screen -> space-bar to select drive, tab to OK, enter to accept.
In this case accept when "[*] sda".

If this also fails, we can begin the process of looking at what is installed and how the booting is configured.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

