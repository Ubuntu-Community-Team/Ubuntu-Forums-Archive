---
title: "Can't find the boot order list."
date: 2023-05-16
forum: General Help
---

### Post by themask23 on 2023-05-16
[FONT=inherit][FONT=inherit][FONT=inherit]I am trying to dual boot windows with xubuntu, and when access my BIOS I cant find the boot priority list. My boot mode is set to legacy.
[/FONT][/FONT][/FONT]

---

### Post by Rubi1200 on 2023-05-16
Hi and welcome to the forums.

Please provide some specs. such as make and type of laptop/computer, version of Windows, version of Xubuntu. The more info you provide, the easier it will be to offer help.

Thanks.

---

### Post by themask23 on 2023-05-16
> **Rubi1200 said:**
> Hi and welcome to the forums.

Please provide some specs. such as make and type of laptop/computer, version of Windows, version of Xubuntu. The more info you provide, the easier it will be to offer help.

Thanks.

[COLOR=#000000][INDENT]Hey! I have DeLL laptop, Windows 10 and the version of Xubuntu i'm downloading is 22.04, the Jammy Jellyfish one I think. And I am not sure if this is relevant but my boot mode is set to legacy[/INDENT]


[/COLOR]
[COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]

---

### Post by ActionParsnip on 2023-05-16
Is the dual boot setup and in place or are you looking to install Xubuntu alongside Windows?

---

### Post by tea for one on 2023-05-16
> **themask23 said:**
> Hey! I have DeLL laptop, Windows 10 and the version of Xubuntu i'm downloading is 22.04, the Jammy Jellyfish one I think. And I am not sure if this is relevant but my boot mode is set to legacy
Windows 10 should be installed in UEFI mode, can you double check?
Start Windows 10 > System Information > System Summary > BIOS mode > UEFI

---

### Post by yancek on 2023-05-16
Was windows 10 installed on the computer when you purchased it?  If so, it is almost certainly an EFI install so you would need to install Xubuntu in EFI mode in order to boot both Xubuntu and windows if they are on the same drive.  If you have windows on one drive and install Xubuntu on another drive you would be able to boot either but would have to do it by making the selection in the BIOS.

>  [FONT=inherit][FONT=inherit][FONT=inherit]when access my BIOS I cant find the boot priority list.[/FONT][/FONT][/FONT]

There should be a tab at the top of your BIOS screen for boot options and if you are using a USB with Xubuntu on it, it should show there, usually by the name of the usb (Sandisk, Toshiba, etc.).  You may have it shown twice, once as UEFI and once as Legacy.  Do you have a bootable Xubuntu USB plugged in when you boot?

---

