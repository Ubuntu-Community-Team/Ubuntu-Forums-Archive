---
title: "os-uninstaller broke windows 8"
date: 2013-02-15
forum: General Help
---

### Post by Jimmt0 on 2013-02-15
I installed Ubuntu alongside my windows 8 (came with the laptop) and then decided to uninstall. At that point it still worked I just wanted the disk space and not the annoying grub menu. So I used os-uninstaller ([https://help.ubuntu.com/community/OS-Uninstaller)on](https://help.ubuntu.com/community/OS-Uninstaller)on) my linux live flash drive to uninstall ubuntu, and it says complete, but now upon selection in the bios of windows boot it just loads forever.

When I start up the computer, I immediately go to the grub line where you can press tab for all commands. I type in reboot and hit f12 to get to bios, where I can choose from windows boot, Ubuntu, ubuntu (yeah it shows 2), 2 ipv... things and my flash drive (not in that order). When I select windows boot that's when it loads forever.

Please help, posting this on trial ubuntu and I miss my laptop :\ Will never use linux again...

---

### Post by oldfred on 2013-02-15
Rather than booting from a grub menu can you boot by directly going into UEFI menu and choosing Windows?

Did you run Boot-Repair? That does rename Windows efi files to allow Ubuntu to boot on those systems that do not implement UEFI correctly. They only let Windows boot. But Boot-Repair will rename back.

If you cannot directly boot Windows from UEFI post this.
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Jimmt0 on 2013-02-15
How would I get to the UEFI menu?
 
EDIT: Still not too familiar with the BIOS. I just boot into the grub command line, and then type reboot, shows the lenovo logo, then I hit f12 and I think I get to the UEFI menu, with windows boot, ubuntu, Ubuntu, etc. I will try boot repair when I get home. However, if that is the UEFI menu, then when I boot windows, it loads infintely.

---

### Post by oldfred on 2013-02-15
This may help?

UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You have to run the BootInfo report from a Ubuntu live installer either DVD or Flash. The one you used to install originally will work or it has full downloads of a repair verson.

---

### Post by YannBuntu on 2013-02-15
Hello

Please run Boot-Repair's Recommended Repair, and indicate the URL that will appear.
Then reboot the PC, and indicate what you observe (if Windows boots ok or not).

---

### Post by Jimmt0 on 2013-02-15
bootinfo from bootrepair: [http://paste.ubuntu.com/1660057/](http://paste.ubuntu.com/1660057/) (before recommended repair)
after recommended repair: [http://paste.ubuntu.com/1660065/](http://paste.ubuntu.com/1660065/)

---

### Post by oldfred on 2013-02-15
From UEFI menu are you booting the Windows entry?

Since drive is gpt partitioned Windows will only boot from efi partition not MBR. You do have a Windows boot loader in the MBR but it will only give errors.

---

### Post by Jimmt0 on 2013-02-15
> **oldfred said:**
> From UEFI menu are you booting the Windows entry?

Since drive is gpt partitioned Windows will only boot from efi partition not MBR. You do have a Windows boot loader in the MBR but it will only give errors.
uh, how do I get to EFI? and why does the UEFI still show 2 ubuntu entries even though I've uninstalled it?

Also: following some onlintutorials, I used the boot repair recommended repair, rebooted, typed reboot on grub, selected windows from bios, and I got to the same screen as if you put in a windows 8 disk (refresh, clean, command prompt, fix boot)...I typed bootrec.exe /fixmbr and bootrec.exe /fixboot but nothing really happened, tried fix boot button also.

---

### Post by oldfred on 2013-02-15
The bootrec tool is to fix BIOS installs, I do not think that works with UEFI.

The UEFI menu saves entries. You have to go into UEFI menu and edit them out.

Post #4 has instructions on what key to use for most systems to get into UEFI directly. Otherwise check your owners manual or vendors on line site for instructions. I thought you used f12 or is that the one time change boot key not the full UEFI/BIOS menu.

One user posted this on editing UEFI entries. You should also have the option to delete entries.
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

           Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

Forum on Windows 8 issues, they should know more about it.
       [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by YannBuntu on 2013-02-17
Hello

> **Jimmt0 said:**
> bootinfo from bootrepair: [http://paste.ubuntu.com/1660057/](http://paste.ubuntu.com/1660057/) (before recommended repair)
after recommended repair: [http://paste.ubuntu.com/1660065/](http://paste.ubuntu.com/1660065/)

Please boot an Ubuntu disk, choose "Try Ubuntu", then open a terminal and type the following commands:

```
sudo mount /dev/sda2 /mnt
sudo rm -rf /mnt/EFI/ubuntu
```

Then reboot the computer, it should boot directly to Windows.

---

