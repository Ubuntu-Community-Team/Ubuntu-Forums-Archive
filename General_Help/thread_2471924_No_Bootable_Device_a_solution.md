---
title: "No Bootable Device a solution"
date: 2022-02-13
forum: General Help
---

### Post by nsaxon-clarke on 2022-02-13
Hi. having installed ubuntu onto my acer aspire laptop I now have the No Bootable Device problem, The solution is on this forum that worked for me but i can't find it. It seamed that some Acer computers put different OS in different places and having replaced windows with linux on reboot the OS could not be found. The solution involved booting with live usb then going into the terminal and in about two lines of code changed where the boot? looked for the OS. I'm sorry i can't give you more details but that solution worked for me when anything else i tried didn't.
Thanks for any help you can give me
John

---

### Post by dragonfly41 on 2022-02-13
Use "Advanced Search" at top right of this page.

Search for "No Bootable Device" in Keywords then drop down menu to select "in titles".

[https://ubuntuforums.org/search.php?searchid=26178942](https://ubuntuforums.org/search.php?searchid=26178942)

[P.S.] you can narrow down the search by using keywords

bootable device Acer

[https://ubuntuforums.org/search.php?searchid=26178980](https://ubuntuforums.org/search.php?searchid=26178980)

---

### Post by MAFoElffen on 2022-02-13
I am guessing that you might be looking for 'efibootmgr', where you probably need to check the EFI boot files, and reset the EFI boot order to you Linux boot files(?)

Like I said, just a guess...

---

### Post by dragonfly41 on 2022-02-13
Read first post after modifying advanced search keywords to include OldFred

No Bootable Device OldFred Acer

This refers to efibootmgr

In fact you can add that as another keyword.

---

### Post by nsaxon-clarke on 2022-02-13
no it's not the boot order

---

### Post by oldfred on 2022-02-13
I find forum advanced search really only works with one keyword. 
If I want multiple keywords I use  google.
site:ubuntuforums.org "No Bootable Device" oldfred Acer
Only 42 reponses including this one. :(
I know I have posted the Acer "trust" issue as one of the most common reasons many more times.

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)

If not "trust" issue in Acer's UEFI and UEFI is updated to most current firmware, post Boot-Repair summary report.
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)            
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by nsaxon-clarke on 2022-02-14
I was wrong the solution was on the MX Linux Forum and posted by hamak :


                        After installing MX Linux on Acer ES1-132 from USB Flashdrive you get **No Bootable Device**

**This was easy fixed by renaming \EFI\BOOT to \EFI\Linux like this:**
after I installed MX Linux 19.3 on my Acer ES1-132 on my /dev/mmcblk0p1 partition i got **No Bootable Device**

boot from usb drive and select menu: **Boot Rescue Menu**
**Find EFI Bootloaders** and hit ENTER
select and start your installed MX Linux from where you installed it, in my case it was: *(hd1,gpt1)/EFI/mx19/grubx64.efi*

open terminal and do this:
sudo su (type in your root password)
mount /dev/mmcblk0p1 /mnt
mv /mnt/EFI/BOOT /mnt/EFI/Linux

unplug USB flashdrive and reboot

Finished !

[B]WHY!
Acer ES1-132 has hardcoded these boot locations[/B]

\EFI\Linux\BOOTX64.efi (Linux)
\EFI\Microsoft\Boot\bootmgfw.efi (Windows Boot Manager)
\EFI\ubuntu\shim.efi (ubuntu SECURE)
\EFI\ubuntu\shim$cpu$.efi (ubuntu SECURE)
\EFI\ubuntu\grub.efi (ubuntu NORMAL)
\EFI\fedora\shim.efi (Fedora)
\EFI\android\bootx64.efi (Android)
\EFI\opensuse\grubx64.efi (topenSUSE)
\EFI\redhat\grub.efi (Red Hat Linux)
\EFI\SuSE\elilo.efi (SuSE Linux)
\EFI\ubuntu\grub$cpu$.efi (ubuntu NORMAL)
--------------------------------------------------------------------------------
I don't know how you change it for unbuntu but it worked for my MX Linux installation
Thanks for the advice and help

---

