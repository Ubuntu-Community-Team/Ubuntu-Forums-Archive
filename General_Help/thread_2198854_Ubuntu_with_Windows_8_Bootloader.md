---
title: "Ubuntu with Windows 8 Bootloader"
date: 2014-01-10
forum: General Help
---

### Post by tketter on 2014-01-10
Hi, after several days of trying what I found on the internet so far I decided to finally ask someone who actually knows something about Ubuntu unlike me.
I want to use Windows 8.1 64Bit and Ubuntu  13.10 64Bit on a Laptop(Asus R704VC) with Windows's bootloader rather than Grub2, because I work with Windows more often.
Both are installed in UEFI-Mode. Secure Boot is disabled for Windows, I do not know if the same is true for Ubuntu. 
Windows was installed first. When I start my Laptop i get the Grub2 screen where I can choose between 7 or 8 options after having executed boot-repair(4 before).
I already achieved to get the Win8 bootloader once, but got the error 0xc00007b when trying to start Ubuntu. Also Windows was not recognized when installing Ubuntu.
boot repair file:[http://paste.ubuntu.com/6730261](http://paste.ubuntu.com/6730261)
sdb is my Ubuntu-live-Stick; sda3 is not partitioned yet.

Maybe someone has an idea what to do, because i cannot think of anything.

Thanks in advance, Kernie

---

### Post by fantab on 2014-01-10
The Boot-Repair utility has renamed you Windows boot file, restoring the original from EFI Backup should solve the issue for you.

Run Boot-Repair again and select the option '**Restore EFI Backups**'... Note the Link created for 'BootInfo summary', and post it back it you have further boot problems.

Reboot.

Windows Boot manager does NOT boot Linux, so you have to use GRUB to dual-boot. EasyBCD is an option to boot Linux from Windows.
However, what you probably want is to set Windows as default boot (Grub boots directly to Windows), which can be easily done later by editing /etc/default/grub file.

First lets get that Windows booting from Grub...

---

### Post by tketter on 2014-01-11
Thanks for the really quick help.
I did what you told me and now i can choose the Windows-boot-loader from grub. And then i have to choose Win8 from the Win-boot-loader. Is there a way to directly load Windows without the extra step(edit: done)?
Sadly my PC crashed while i was writing and the BootInfo-Link is not available now.
And there is no way to do something like [this(second post)]("http://askubuntu.com/questions/230878/dual-boot-windows-8-and-ubuntu-with-windows-8-boot-manager")?

---

### Post by fantab on 2014-01-11
> **tketter said:**
> ... i can choose the Windows-boot-loader from grub. And then i have to choose Win8 from the Win-boot-loader. 

I don't understand.
Do you have some other boot loader for Win8 other than the Window's default?

We need to look at that 'BootInfo Summary'. Run Boot-Repair again and 'create a Bootinfo Summary'... No need to run repairs now.

Yes, you can use EasyBCD from Windows but I don't know how it works... I've never used it.

---

### Post by tketter on 2014-01-11
First Problem is fixed already. The problem was that after choosing the option in grub that would boot Windows i got another screen, where i had to choose Windows 8 as OS to boot. 
I assume it was the Windows bootloader as that was the option I chose in grub.

To the second problem: I just want to get the blue Windows screen insted of grub's. The Link was just an example. The way to get to the end does not really matter to me.
[URL="http://paste.ubuntu.com/6732672/"]
BootInfo[/URL]

---

### Post by fantab on 2014-01-11
You know that we can customize Grub 'appearance'?
If you don't, then you must read this: [http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Checkout:
 [http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/)
[https://neosmart.net/forums/](https://neosmart.net/forums/)

---

### Post by tketter on 2014-01-11
I have not known that, but I will try it.

This matter is done then.

Thanks for your help. I really appreciate it.

---

### Post by oldfred on 2014-01-11
With UEFI you do not need EasyBCD. 
EasyBCD is a boot manager which then allows Windows to boot other systems. And grub is both a boot manager and boot loader. But UEFI is also a boot manager and you can from either UEFI menu or one time boot key choose which system to boot.
So with both Ubuntu & Windows in UEFI mode you can as booting choose which system to directly boot. In UEFI set Windows as default if you use that the most. Then go into UEFI or use one time boot key and choose Ubuntu when you want it.

---

