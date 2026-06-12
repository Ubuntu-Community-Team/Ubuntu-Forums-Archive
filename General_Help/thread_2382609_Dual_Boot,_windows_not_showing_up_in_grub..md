---
title: "Dual Boot, windows not showing up in grub."
date: 2018-01-15
forum: General Help
---

### Post by shad0s on 2018-01-15
Hello everyone. Im pretty new at Linux and bash commands so I'm sorry if I sound incompetent or don't give enough detail. I successfully installed Kubuntu along side Windows 10. I have two hard drives, one with Windows 10(1TB) And another with Kubuntu (160gb). The install went fine and I was originally able to boot changing the device from Windows boot manager to the hard drive with Linux. I tried to boot into Linux this morning and found a blinking cursor with nothing else. Being a noob, but a knowledgeable Google searcher I came up with my live installation and ran boot repair, and rebooted. Now I can boot into grub just fine, but my windows option is nowhere to be found in grub. Strangely, now every boot device in my bios, the two hard drives, and Windows boot manager, takes me into grub. I tried running update-grub and rebooting, it still didn't change. I tried boot repair twice, one in live the other on an actual boot repair disk.

My hardware is as follows:
MOBO: Asus Prime b350 plus
GPU: Nvidia GTX 1060TI 6GB
CPU: Ryzen 5 1600
Ram 8 GB Corsair, not sure of model

I uploaded the log boot repair gave me, and the URL is as follows.

[https://paste.ubuntu.com/26393464/](https://paste.ubuntu.com/26393464/)

I'm sorry If I didn't give enough detail or I gave too much, any help is greatly appreciated.

---

### Post by oldfred on 2018-01-15
It looks like you have a newer UEFI system.
But Windows and Ubuntu are both installed to MBR partitioned drives, not the gpt partitioning used with UEFI.
And Windows then only can boot in BIOS mode from UEFI.

You also are missing the Windows Boot partition which has two essential boot files.
Was system booting from sdb and Windows boot partition was on it.
Normally Windows boot partition is on same drive as main install in 100MB partition.
 Vista/7/8/10 BIOS (with 7, 8 or 10 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe  

You are missing first two files, but you can use a Windows repair disk or installer with repair console and with full set of Windows repairs,add those files to sda1. You cannot fix from Ubuntu.

 f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html) 

[https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues](https://support.microsoft.com/en-us/help/927392/use-bootrec-exe-in-the-windows-re-to-troubleshoot-startup-issues)

With two drives do not run Boot-Repair's auto fix. Only use advanced mode and keep Windows boot loader on Windows drive and grub on Ubuntu drive. Set BIOS to default boot from Ubuntu drive.
Then when Windows has issues like turning fast start up back on (when it does updates) or needs chkdsk, you can directly boot from BIOS and select to boot Windows drive.
Grub only boots working Windows.

---

