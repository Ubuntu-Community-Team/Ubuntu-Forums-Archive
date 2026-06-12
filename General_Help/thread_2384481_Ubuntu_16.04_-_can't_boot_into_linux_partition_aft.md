---
title: "Ubuntu 16.04 - can't boot into linux partition after grub2 update"
date: 2018-02-07
forum: General Help
---

### Post by ppcubu on 2018-02-07
Hi,

I'm running Ubuntustudio 16.04 as dual boot system with Windows10 on a HP Envy dv7 laptop.

I booted into Ubuntu and had some system/software updates, which I installed and noticed there was a grub update included.
While installing the updates the machine just rebooted and I can't boot into Ubuntu anymore.

Going into boot options, and choosing the ubuntu partition, I get a grub command line prompt.

I tried to solve the issue with [https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux)

output of **set** command:
[ATTACH=CONFIG]278472[/ATTACH]

Then I tried the following commands ( from above article )
[I]grub> set root=(hd2,gpt2)
grub> linux /boot/vmlinuz-xxxxxxxx-lowlatency **root=/dev/sda1**
grub> initrd /boot/initrd.img-xxxxxxx-lowlatency
grub> boot[/I]

I'm not sure about **root=/dev/sda1** though, I also tried **root=/dev/sda2**

Both times I get the following output:
[ATTACH=CONFIG]278471[/ATTACH]


So I'm completely lost
and I'd appreciate any help :-)

Thanks
Regards

---

### Post by oldfred on 2018-02-07
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by ppcubu on 2018-02-08
Hi,
Thanks for answering.

I managed to boot into the linux partition,
but now I'm stuck.

I cannot install the Boot Repair application.

A software update containing a grub update crashed,
and so does a **dpkg --configure -a**, which is required to continue.

If I'm not able to remove that grub update, then I'm stuck with a broken system.

---

### Post by oldfred on 2018-02-08
Can you still run live installer?

---

### Post by ppcubu on 2018-02-09
I ran live installer and created boot info:
[https://pastebin.com/WsXH4wVR](https://pastebin.com/WsXH4wVR)

I can boot into ubuntu partition from grub command line with the following:
[B][I]set root=(hd2,2)
linux /boot/vmlinuz-4.4.0-112-lowlatency root=/dev/sdc2
initrd /boot/initrd.img-4.4.0-112-lowlatency
boot[/I][/B]

Thanks for your help and time.
Regards

---

### Post by oldfred on 2018-02-09
Is sdc an external drive?

You show correct entry in UEFI for Ubuntu. It normally has two entries one shim and one grub. Shim should work if UEFI Secure Boot is on or off. Grub entry will only work if Secure Boot is off.

But you have an HP. And install and ESP - efi system partition is on sdc?
Did you disconnect sda & sdb to get ESP on sdc or did installer actually let you put ESP on sdc and Ubuntu's boot files in the ESP on sdc?  I have tried and it has not worked for me.

Your Windows UEFI boot entry uses ESP on sda, and Ubuntu entries use ESP on sdc, so that looks correct.
Can you  directly boot Ubuntu entry from UEFI boot menu or are you having to manually boot each time?

HP violates UEFI spec which says NOT to use description as part of UEFI boot. And only valid description is "Windows Boot Manger". But multiple work arounds depending on configuration.
Many found hard drive or fallback UEFI entry of /EFI/Boot/bootx64.efi works. That is the required entry for external drives, but also works on internal drives.
HP typically has that entry where bootx64.efi is just a copy of Windows .efi boot file.
Many make bootx64.efi a copy of shimx64.efi from /EFI/ubuntu folder. Not sure if in your case you can do that on ESP in sdc or need to do that on ESP in sda?
Boot-Repair now automatically does copy and backs up current bootx64.efi, but not sure which ESP it will do it on, or if you have a choice.

Others use rEFInd or add an entry into Windows BCD to cause system to reboot and one time boot something else which also seems to work. Or they just use UEFI boot menu. It may depend on whether regularly booting both systems or mostly booting one or the other.

Details on multiple work arounds in link in my signature below. Some examples of those work arounds in HP specific threads.
Users had to manually copy files before Boot-Repair did auto copy.
 HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
      
 Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227)
HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)

---

### Post by ppcubu on 2018-02-10
Sdc is an internal drive.

I don't remember how the install precisely went,
but I do remember that it took a lot of effort and perseverance to turn this laptop into a dual boot,
also vowing to myself never to buy an HP again, since they don't make things easy.

I can boot directly into Windows, which I hardly use,
but I can't boot directly into Ubuntu, it is each time a four line entry on grub command line to manually boot.

For the moment I'm considering leaving things as they are: I can do my work.
( although this machine is then stuck in time, since I can't update the system anymore due to a broken Grub2 update )

I'll read up on rEFInd.

Thanks.
Regards

---

### Post by oldfred on 2018-02-10
Somewhat off topic rant.

I am retired and do not need a laptop.
And I am somewhat anti-laptop. I know I am trying to sweep the sea back with a broom.

I do not find laptops ergonomic. When on desk keyboard is too high, screen too low. And screen size is a lot smaller. Many add another larger screen when using laptop on desk and may add keyboard, converting laptop to desktop.
While every generation of laptops is promoted as desktop equivalent, then never are. But they are lower power.
They are difficult to repair and not flexible on adding extra drives or updating video card.

I found building my own system with desktop motherboard works the best. While the motherboad vendors usually say they do not work with Linux, they work the best of all systems.
I do have an now older Dell Haswell based SFF small desktop that works well also. I mostly use Windows on it, as it is for watching TV and Linux does not have the DRM rights management. I just saw Firefox now has a sandbox with the DRM and may work, so I want to experiment with that.

---

### Post by ppcubu on 2018-02-10
True,

I also build my own desktops,
but laptops have that one convenience :-)

Thanks for your help.

---

### Post by ppcubu on 2018-02-17
As an addendum,

I fixed grub with the following commands:

update-grub
grub-install /dev/sdc

---

