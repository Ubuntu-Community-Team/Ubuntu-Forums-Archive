---
title: "error occurred during boot repair"
date: 2014-05-12
forum: General Help
---

### Post by camclark715 on 2014-05-12
I am running a dual boot system and every other time with installing a new distro, after installing I run boot repair and it sets grub as the default boot screen. 

After installing Ubuntu 14.04 every time i have tried to run boot repair I get the following:

An error occurred during the repair.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7454901/](http://paste.ubuntu.com/7454901/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] 

You can now reboot your computer.

I have an hp Pavilion dv4t-5100. I am fairly new to linux so I dont know what other information is needed.

Thanks in advance!

---

### Post by oldfred on 2014-05-13
I am not sure why Boot-Repair reports an error. I see that with others that then have worked.

And grub is saying it installed ok as error is 0.

 grub-install /dev/sda: exit code of grub-install /dev/sda:0

Can you in UEFI menu choose ubuntu entry?


```
 BootOrder: 0001,2001,3003,3001,3002,2002,2003
Boot0000* Notebook Hard Drive
Boot0003* Windows Boot Manager
Boot0004* USB Hard Drive -         USB Flash Memory
Boot0005* USB Hard Drive (UEFI) - USB Flash Memory
Boot2001* USB Drive (UEFI)
Boot2002* Internal CD/DVD ROM Drive (UEFI)
Boot3001* Internal Hard Disk or Solid State Disk
Boot3002* Internal Hard Disk or Solid State Disk
Boot3003* Internal Hard Disk or Solid State Disk
Boot0001* ubuntu.


```

But some HPs are modified to only boot Windows.
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

---

