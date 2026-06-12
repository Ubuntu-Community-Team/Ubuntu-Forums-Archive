---
title: "Dual boot: GRUB gets replaced by Windows boot manager after booting into Windows"
date: 2021-02-17
forum: General Help
---

### Post by johan-k on 2021-02-17
Hello there,

I've been experiencing something strange on my desktop pc, which I never used to have. After I install a Linux distribution (have tried Ubuntu 20.04, Fedora 33), when rebooting after install the GRUB boot menu shows and I can select Linux or Windows. As long as I keep going into Linux, all good. As soon as I boot into Windows 10 (20H2) and I reboot, GRUB is gone and replaced by the Windows boot manager (which isn't showing Linux, of course). First I thought this happened because of some Windows update got installed, but it happens all the time. I have two drives, a SSD one which holds all the Windows partitions, and a regular HDD which holds a NTFS partition and the Linux root and swap partitions. I've tried installing GRUB on either drives but that didn't seem to make a difference. What can I do about this, unfortunately I do need Windows still ;)?

Regards,

Johan

---

### Post by yancek on 2021-02-17
Are both windows 10 and Ubuntu UEFI installs?  If so run the following commands and post the output here which will help others to help you.

>  sudo efibootmr -v
cat /etc/grub/defualt

Doing a quick online search, this seems to have been a problem for years and many of the threads I have seen are in regard to Lenovo?

---

### Post by oldfred on 2021-02-17
Is this an HP?
Many with HP have said they have to update UEFI and then only changing boot order in UEFI settings, not boot menu works.
Not sure if this is same as next paragraph.

Many have to add a BCD entry as it may be Windows is working with UEFI and updating boot order every time. 
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
undo:
bcdedit /set {bootmgr} path \EFI\Microsoft\Boot\bootmgfw.efi

Be sure to create a Windows repair/recovery flash drive as changes to Windows can prevent it from booting.
And grub only boots working Windows, so if you cannot directly boot Windows from UEFI, you have to use repair/recovery flash drive.

---

### Post by yancek on 2021-02-17
I have two HP laptops, one about 4 years old and one is a few months old.  Both are UEFI.  I have never updated the firmware on either and have had no problems installing various Linux Operating systems.  I have not needed to modify the BCD entry either.  One thing is that changing the boot order with efibootmgr has never worked but that is simple in the BIOS firmware.  Currently have Slackware, Ubuntu, PCLinuxOS and Lubuntu on them.  Might just be lucky.

---

### Post by oldfred on 2021-02-17
@yancek
Good to know. Seen may who have updated & then used UEFI/BIOS to change boot order with HP. Thought that UEFI update required.
But I do suggest UEFI update for many reasons. The listed changes with an update are not always all the fixes the vendor is making.

This is one reason, UEFI/BIOS, and all operating systems have needed updates for these:
Spectre virus, repoline
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by johan-k on 2021-02-18
Hi all,

Thanks for responding. It's a self-built desktop and the BIOS is at the latest possible version. I will install a Linux distro once again and run the commands and update the ticket.

---

### Post by johan-k on 2021-02-18
sudo bootmgr -v
BootCurrent: 0001
Timeout: 4 seconds
BootOrder: 0001,0002
Boot0001* ubuntu    HD(2,GPT,f6ece7b6-6f2b-424c-89a1-d3d8d43cbf50,0x109000,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot0002* Hard Drive     BBS(HD,,0x0)AMGOAMNO........o.C.T.2.5.0.M.X.5.0.0.S.S.D.1....................A...........................>..Gd-.;.A..MQ..L.8.1.5.1.1.E.6.3.5.8.9.8. . . . . . . . ......AMBOAMNO........o.W.D.C. .W.D.2.0.E.A.R.S.-.0.0.M.V.W.B.0....................A...........................>..Gd-.;.A..MQ..L. . . . .W. .-.D.M.W.Z.A.1.A.1.8.7.7.4.8......AMBO


Forgot to upload the grub content to my cloud :( And of course, after booting to Windows, Mint/Grub is nowhere to be seen again. At least it's consistent!

So, I installed the bootloader onto /dev/sda and the Windows boot manager is on /dev/sda2.

---

### Post by CelticWarrior on 2021-02-18
> [COLOR=#000000][INDENT]So, I installed the bootloader onto /dev/sda and the Windows boot manager is on /dev/sda2.[COLOR=#222222]

How? Why?
In UEFI all bootloaders should reside in the ESP (EFI System Partition).
And 'bootmgr -v' is a typo, isn't it? It should be 'efibootmgr -v' (no sudo required).
And there's no Windows boot manager list which suggests it may have been installed in Legacy ("BIOS") mode, perhaps? If its drive is MBR then it certainly is in Legacy mode. Windows is strict about MBR for Legacy("BIOS") or BIOS hardware installations and GPT for UEFI mode.

And, finally (for the moment), is it Ubuntu or Mint?[/COLOR][/INDENT]


[/COLOR]

---

