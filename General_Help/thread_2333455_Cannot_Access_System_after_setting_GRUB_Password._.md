---
title: "Cannot Access System after setting GRUB Password. Please help urgently"
date: 2016-08-10
forum: General Help
---

### Post by Rahul_Mukherji on 2016-08-10
[COLOR=#111111][FONT=Ubuntu]Since I realised that GRUB is not password protected, I have been slightly concerned, as any can get access to my system configuration. I decided to act on it, and followed the instructions in this answer:[How to add the GRUB password protection to the OS load process instead of when editing boot options]("http://askubuntu.com/questions/370693/how-to-add-the-grub-password-protection-to-the-os-load-process-instead-of-when-e")[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I rebooted, and the GRUB screen showed. I booted into Ubuntu, and was prompted for a username. I entered the credentials (username:root, password: the one I set in the make password command). It simply took me back to the GRUB menu. I thought I entered them wrong so I reentered them. Still no luck. I am now locked out of my system. I am very sure that my password is correct. Is there any way to resolve this situation?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu](Note: **I am using GRUB Legacy, not Grub2**, and modified the commands as such)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]UPDATE: I have a Windows 10 partition on my machine. I now realise that it was still possible to access system configuration by pressing the F2, F11 and F12 keys. I have booted into the Windows 10 partition. Is there any way to access and rescue my Ubuntu partition from there? Please answer as soon as possible. (Is it possible to recover my system using LiveCD?)[/FONT][/COLOR]

---

### Post by yancek on 2016-08-10
The question at the link you posted is how to set a grub password on Grub Legacy.  The response explains how to do it with Grub2.  The link below explains how to do it with Grub Legacy.  Note the differences.

 [https://linuxconfig.org/set-boot-password-with-grub](https://linuxconfig.org/set-boot-password-with-grub)

Are you using Ubuntu and if so, which release?  Ubuntu has been using Grub2 since 9.10.  Did you set up a root user?

---

### Post by boxcorner on 2016-08-10
I don't know whether this would help, but might be worth considering, if you aren't already aware of it : 

Boot-Repair [http://Boot-Repair](http://Boot-Repair)

---

### Post by oldfred on 2016-08-10
Boot-Repair will not repair grub legacy issues. It was developed long after Ubuntu converted to grub2.
But it has a very good Summary Report so we can see full configuration.

If you can use F-key to boot Windows when grub is installed it sounds more like a new UEFI system with Windows in UEFI boot mode and Ubuntu in BIOS boot mode. But grub legacy does not work with UEFI's gpt partitioned drives.

---

