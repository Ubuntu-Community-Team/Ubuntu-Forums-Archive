---
title: "Grub setup question"
date: 2020-12-30
forum: General Help
---

### Post by paullangdon678 on 2020-12-30
Good evening I have just installed Ubuntu 20.04.1, alongside Windows and Steam OS. Obviously I will be able to lose windows soon when work and other apps permit :-)
I have three different boot options:
1) Ubuntu (SATA6G:Toshiba DT01)
2) SATA 6G_1: ST500DM002-1BD14
& 3) Windows Boot Manager (SATA 6G-2-1BD14)

Windows and Ubuntu are on the same hard disk, Steam is on another.

My most successful is 1): with this I get Windows 10 and Ubuntu as options
With 2) I can get into Steam and after a bit of complaining Ubuntu as well
With 3) I go straight into Windows 10.

What I am trying to achieve is a choice of all three: Steam,Ubuntu and Windows.

I may be a long way off what I need to do but I think I need to edit grub to add in 'Steam' ? I am looking at this [https://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](https://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)
but need a bit of guidance. Or maybe I cannot do better as I have Steam O/S on a separate disk.

---

### Post by oldfred on 2020-12-30
Are they all installed in same boot mode, all UEFI or all BIOS?

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by paullangdon678 on 2020-12-31
Good morning Oldfred and thanks for the reply. 
Here is my Boot-info summary report: 
 [https://paste.ubuntu.com/p/sqbcqnWctB/](https://paste.ubuntu.com/p/sqbcqnWctB/)
  I am sorry but I am not sure if they all installed in same boot mode, all UEFI or all BIOS? I expected to received some messages when installing that suggested not.

---

### Post by yancek on 2020-12-31
Your windows and Ubuntu installs are both UEFI and installed on a GPT drive while Steam OS is a Legacy install on a non-GPT (msdos) drive.  Have you tried running sudo update-grub from Ubuntu?  If not, do it and watch for output for Steam.  You can see the entries for EFI for Ubuntu/windows beginning on line 62 of boot repair.  Beginning on line 5, it shows Grub in the MBR of the Steam drive which would not be necessary on an EFI install but is required for a legacy install.

Lines 122-145 show the efi entries and there is none for Steam as it is a legacy install.  Beginning at line 109 it shows all 3 systems detected. 

Your boot repair output does not show the grub.cfg contents for either Steam or Ubuntu so ...?

I don't have any legacy machines to test but I believe you should be able to boot a legacy install of Linux (Steam) from an EFI install of Ubuntu so do the update-grub on Ubuntu.  You could also try booting Ubuntu, mounting the Steam partition, accessing the /boot/grub/grub.cfg file there and getting the first menuentry for Steam and copying it to the /boot/grub/grub.cfg file on Ubuntu, save the change and reboot without running update-grub.  Lot simpler to run update-grub to see if that does the job though.

---

### Post by oldfred on 2020-12-31
UEFI & BIOS are not compatible. They write system info differently to drive for operating system to use.
You have to reboot to switch or only boot from UEFI/BIOS boot menu.

Some UEFI boot managers may be able to boot a legacy install, but they are really using UEFI's one time reboot feature to boot into BIOS mode. Grub does not have that capability.

How you boot install media for both Ubuntu & Windows is then how it installs or repairs.  You just have to be consistent in how you boot. With installer it is your selection in UEFI boot menu.
Once a system is installed it boots in the default mode you have set in UEFI settings. But most systems now will try to boot any boot entry and seem to work with UEFI or BIOS. 
But if UEFI Secure Boot is on, then only UEFI boot options of signed boot loaders & kernels are allowed.

---

### Post by paullangdon678 on 2021-01-01
oldfred & yancek thanks for the replies. That does make things a lot clearer.
I have however simplified my life and removed Steam OS as it did not work at all with any of my current games (it should do according to Steam).
My apologies - I should have tested Steam OS BEFORE asking for assistance but on the plus side I have learnt something.
Thanks again for the assistance. I may be posting for help with sound shortly...

---

### Post by tea for one on 2021-01-01
> **paullangdon678 said:**
> I have however simplified my lie and removed Steam OS as it did not work at all with any of my current games (it should do according to Steam)

Did you know that you can install the Steam software in Ubuntu and play games without the separate Steam OS?

Here are a couple of links and I'm sure that there are many others:-

[https://www.omgubuntu.co.uk/2016/06/install-steam-on-ubuntu-16-04-lts](https://www.omgubuntu.co.uk/2016/06/install-steam-on-ubuntu-16-04-lts)
[https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-steam-on-ubuntu-20-04-focal-fossa-linux)

---

### Post by paullangdon678 on 2021-01-01
Thanks tea for one,

I have realised and am now trying it out. Game one playing very nicely, which is promising (played very poorly on SteamOS) and really appreciating the support on here :-)

---

