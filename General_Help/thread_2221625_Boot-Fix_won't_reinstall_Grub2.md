---
title: "Boot-Fix won't reinstall Grub2"
date: 2014-05-03
forum: General Help
---

### Post by john204 on 2014-05-03
I had to do a factory reset on my laptop.

Now, all I can get to is my Windows 8.1 partition.  I've tried reinstalling Ubuntu 14.04 from the live USB, and I've tried using bootfix to reinstall Grub2.  Nothing works.

I have a link that shows the entire log from the bootfix operations.

[http://paste.ubuntu.com/7384811/](http://paste.ubuntu.com/7384811/)

Can anyone help?  I'm at the end of my rope with this.

Thanks in advance.

---

### Post by oldfred on 2014-05-03
What happens when you boot the ubuntu entry from UEFI menu?
Have you tried with secure boot off?
What computer & model?

Some brands/models of computers have modified UEFI to only boot Windows.

       **Systems that only boot Windows from UEFI. Often Sony & HP, maybe others**
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find this changing this to be shim or grub /EFI/Boot/bootx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   Boot_Repair - Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by john204 on 2014-05-03
Thank you for responding. Actually, a few hours ago, I took a risk and stumbled upon a solution. I just hadn't gotten around to posting it yet.  

I reinstalled Ubuntu, only this time I went into the partition manager and deleted the EFI partition. Then, I immediately created the same partition again. 

This allowed my install to be successful.

Hope this helps somebody else in the future, and thanks again.

---

