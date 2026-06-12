---
title: "Dual Boot: Windows 10 (bitlocker) and Kubuntu 16.10 on UEFI"
date: 2016-10-01
forum: General Help
---

### Post by altaaa on 2016-10-01
Hi forum,

I'm trying to set up a dual boot of Windows 10 and Kubuntu 16.10 on my work laptop. I shrunk the Win10 partition, installed Kubuntu and it all worked like a charm (with GRUB). However I am forced by policy to have my Win10 partition encrypted with BitLocker. So that rules out any bootloader other than the Microsoft one. I can see the Kubuntu installer created an UEFI boot manager next to the Windows boot manager. If I boot that one (it's just called "ubuntu") I get the GRUB menu which allows me to boot Kubuntu and Windows. But Bitlocker will not function because the whole boot-chain needs to be trusted. So my only option is to boot from the Windows Boot Manager (\EFI\Microsoft\Boot\bootmgfw.efi). 

After some Googling I found several posts and articles detailing some steps to add the Linux install as a boot option in the Windows bootloader. For example, [https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](https://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/).

in short:
- extract the boot record of the Linux partition with ```
dd if=<partition where Linux is installed> of=<output file> bs=512 count=1
```
- copy the output file to the Windows partition C:\
- in Windows, use bcdedit to add a boot entry which is linked to that output file ```

bcdedit /create /d "Kubuntu" /application bootloader
bcdedit /set {id} device partition=C:
bcdedit /set {id} path \kubuntu.bin
bcdedit /displayorder {id} /addlast
bcdedit /timeout 30

```

When I restart I get the Metro boot loader screen with the two options, Windows and Linux, and Windows seems to work fine. Linux however gives me a 0xc000007b error message.

Is there any known way for me to boot into Kubuntu 16.10 through the Windows bootloader?

---

### Post by oldfred on 2016-10-02
I think those instructions are for BIOS? And with grub installed to a partition not to MBR, which Ubuntu/grub does not recommend.
But with UEFI, you can use the one time boot key in UEFI to choose which system to boot.

But if a company system, do you have permission to install another system?
Some companies consider it an automatic termination to modify company property. 
And if encryption required, they should have totally locked down UEFI, so you cannot boot any other system.

You can possibly use a flash drive to boot Ubuntu, if that is allowed. But you still have to set flash drive as first in boot order, then Windows. So if flash drive not plugged in it boots Windows.

---

### Post by altaaa on 2016-10-02
oldfred, we do not have such restrictions, we can install other OS if we choose, but we do state bitlocker needs to be enabled. It's not technically enforced but through company policy.

I can use one-time boot key to get into Kubuntu, if that's the only way it's fine. I just wondered if there was any way to boot Kubuntu through the windows boot menu.

---

### Post by oldfred on 2016-10-02
I do not know with bitlocker if adding a BCD entry works or not.
I believe the BCD entry has you boot into Windows to load BCD and then Windows resets UEFI using UEFI's one time boot to reboot into Ubuntu. May be easier just to use UEFI?

       Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

### Post by yancek on 2016-10-02
I used the method you describe in your original post to boot Kubuntu from windows 10 as a test.  It worked but certainly isn't as simple as using Grub but this was an MBR system.  If you look at the commands, you can see that it will not work with UEFI so your current method of the one time boot key may be the best option.  I'm not familiar with UEFI so maybe oldfred or someone else will have a suggestion.

---

### Post by altaaa on 2016-10-02
oldfred - those commands replace the windows boot manager, which will prevent bitlocker from functioning.

yancek, the commands are indeed for MBR. I also believe the one time boot key is the way to go here.

I activated BitLocker and everything works okay, I can boot into Windows or Kubuntu by pressing F12 on startup. Thanks for the help so far, I guess its "case closed" ;-)

---

