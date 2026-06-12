---
title: "Windows 10 UEFI Not Showing in Grub2"
date: 2018-08-24
forum: General Help
---

### Post by BigBig5 on 2018-08-24
With Ubuntu, Grub2 menu doesn't show Windows 10. I tried [this]("https://ihaveabackup.net/article/grub2-entry-for-windows-10-uefi") but when I do*** sudo grub-mkconfig -o /boot/grub.cfg*** it outputs:
```
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.15.0-33-generic
Found initrd image: /boot/initrd.img-4.15.0-33-generic
Found linux image: /boot/vmlinuz-4.15.0-29-generic
Found initrd image: /boot/initrd.img-4.15.0-29-generic
Adding boot menu entry for EFI firmware configuration
/etc/grub.d/40_custom: 1: /etc/grub.d/40_custom: menuentry: not found
/etc/grub.d/40_custom: 2: /etc/grub.d/40_custom: search: not found
/etc/grub.d/40_custom: 3: /etc/grub.d/40_custom: Syntax error: word unexpected (expecting ")")
```

What am I doing wrong? Also, os-prober doesn't work with uefi.

---

### Post by oldfred on 2018-08-24
How did you edit 40_custom? You do not remove lines at top and must use valid grub boot stanzas.

Typically os-prober will not see Windows if Ubuntu not installed in same boot mode, or both UEFI or both BIOS boot. Or if Windows 8 or 10 has fast start up or always on hibernation set. And Windows updates will turn the fast start up back on, so when grub does not boot Windows directly boot Windows from UEFI and turn fast start up off again.

       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 
    
Boot-Repair will not show the  40_custom with the problem.
Post this in code tags, easy to use with Forum's advanced editor & # icon.
sudo cat /etc/grub.d/40_custom

---

### Post by BigBig5 on 2018-08-24
> **oldfred said:**
> How did you edit 40_custom? You do not remove lines at top and must use valid grub boot stanzas.

Typically os-prober will not see Windows if Ubuntu not installed in same boot mode, or both UEFI or both BIOS boot. Or if Windows 8 or 10 has fast start up or always on hibernation set. And Windows updates will turn the fast start up back on, so when grub does not boot Windows directly boot Windows from UEFI and turn fast start up off again.

       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) 
    
Boot-Repair will not show the  40_custom with the problem.
Post this in code tags, easy to use with Forum's advanced editor & # icon.
sudo cat /etc/grub.d/40_custom

I have fixed this. I had to convert my Windows to from mbr to gpt.

---

