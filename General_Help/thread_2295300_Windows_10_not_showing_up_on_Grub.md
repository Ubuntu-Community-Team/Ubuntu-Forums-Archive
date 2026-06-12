---
title: "Windows 10 not showing up on Grub"
date: 2015-09-17
forum: General Help
---

### Post by Anviori on 2015-09-17
Hello,
Yesterday I tried to dual boot Ubuntu with Windows 10.
I created a separate partition for Ubuntu and installed it on that partition.
Once the instillation was done and I rebooted, Grub does not give me the option
to boot Windows 10; only Ubuntu.
I tried using the boot repair disk but that did not solve the problem.
This is the link that i got after using the boot repair disk: [http://paste.ubuntu.com/12438639](http://paste.ubuntu.com/12438639)

---

### Post by swatto on 2015-09-17
You need to turn off hibernate mode in power options on Windows 10 (this is enabled by default to allow for faster booting - a quick search on Google will explain this). Once done run a live Ubuntu CD and use the grub repair tool, it will then pick up your Windows 10 installation amongst other things. You can then use grub customizer to get rid of the extra entries it has picked up that you don't need.

Hope that helps

---

### Post by Anviori on 2015-09-17
I see, thank you for replying.
The problem is that I do not know how to boot into window since the only OS that grub lets me boot into is Ubuntu

---

### Post by swatto on 2015-09-17
Look at your bios, if your machine is fairly new you should have something called BSS boot priority (this is different from boot priority order) - it will currently be set to Ubuntu but you can switch it to 'Windows Boot Loader' and then boot into windows.

---

### Post by Anviori on 2015-09-17
I just booted into my bios and I don't see anything called the BSS boot priority.
I don't see anything that says Ubuntu or Windows Boot Loader.
I have a Lenovo y50 in case that helps...

---

### Post by swatto on 2015-09-17
Hmm in out at the moment but it should be near where the boot priority order stuff is, I'll have a look when I get home tonight.

---

### Post by oldfred on 2015-09-17
You have BIOS based installs. So MBR of drive controls booting.
With newer systems usually installs are UEFI and UEFI is also a boot manager where you can select which system to boot.

So you will have to temporarily install a Windows boot loader to directly boot into Windows to turn off the always on hibernation of fast start up. Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk. Best to have a Windows repair flash drive to make repairs when needed.

You can use Boot-Repair to put a Windows like boot loader into the MBR. Then restore grub with Boot-Repair also.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation

      [/URL]
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Grub2's os-prober also has not been updated to find Windows 10, so entry will not read Windows 10, but should be something about Windows.

    [URL="http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"]
[/URL]

---

### Post by Anviori on 2015-09-17
So, the problem is fixed!
I used the command: sudo update-grub
It allowed me to go back into Windows and turn hibernation off.
I make a recovery disk just in case and re ran the boot-repair. Everything is working perfectly now. 
Thanks for all the help!

---

