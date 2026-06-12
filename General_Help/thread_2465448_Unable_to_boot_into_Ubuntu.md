---
title: "Unable to boot into Ubuntu"
date: 2021-08-02
forum: General Help
---

### Post by madhu on 2021-08-02
Hello, 

I am using Ubuntu alongside Windows. I am unable to load Ubuntu.

I am not sure whether it is GRUB issue.

At the time of booting, I see the option to select Ubuntu (legacy or UEFI). When I choose UEFI mood it tries to load Ubuntu but after a while I see only a command line blinking cursor in the screen (and it is displayed infinitely). When I select Ubuntu to load on Legacy mode, it shows 'grub rescue>'. So I used Ubuntu Live USB (in UEFI mode) and ran GRUB repair. But it seemed to change nothing. GRUB repair log is here [https://paste.ubuntu.com/p/cs5B6sSdzJ/](https://paste.ubuntu.com/p/cs5B6sSdzJ/) . 

Can someone help me understand what to do further?

Thanks in advance!

---

### Post by yancek on 2021-08-02
Line 285 shows an EFI entry for Ubuntu in the BIOS firmware.  Can you access the BIOS boot options, this would be  done before you see the Grub menu.  The key(s) you use to do this vary with manufacturer so you will have to watch the screen on boot as it usually shows which key to use.  Boot repair shows you have windows 10 on sda4 (line 267 of boot repair)  but also shows w2k or xp on sda9, Line 237.  Is that orrect?  I don't think an EFI install will boot w2k or xp.  Starting at Line 277, you are shown the various EFI options which include windows 10 and Ubuntu.  Ubuntu is shown on Line 287 so when you access the BIOS, select that option and see what happens.

Line 453 shows that the root filesystem was on sda11 during installation and that Ubuntu EFI files were on sda10.  Boot repair shows sda10 as the root filesystem for Ubuntu, beginning at Line 244  Line 455 shows /boot/efi on sda10 but that is the Ubuntu partition and there are no efi files there.

Since you have windows installed UEFI, I would suggest you reinstall Ubuntu to sda10 and let it install the default UEFI files which would create another directory named ubuntu on sda2 containg the EFI boot files for Ubuntu.  Before beginning the reinstall of Ubuntu, I would suggest you read the information at the link below which is the official Ubuntu documentation on dual booting with windows 10 UEFI.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2021-08-02
It looks like the reinstall of grub worked.
You have at some time incorrectly installed grub in BIOS mode and it added a bios_grub partition and grub in gpt's protective MBR.
Just do not boot in BIOS mode, and old grub in MBR will never be used. You can delete the bios_grub partition, currently sda8, but always check before deleting. The bios_grub has to be unformatted, which then shows as an error. Ignore all those errors in report.

If still issues, then perhaps a video issue?
Can you boot recovery mode from grub menu.
If menu does not appear, press escape key (perhaps more than once) right after UEFI/BIOS screen & before grub menu would normally appear. 
If UEFI fast boot on, you may not have time to press any key, make sure it is off in UEFI settings.

What video card/chip?

---

### Post by madhu on 2021-08-02
Thanks for the suggestions!

It turned out that there was not enough space in disk which prevented me from seeing the login screen. 

I am able to login in after I deleted some of files through command line in the recovery mode.

---

