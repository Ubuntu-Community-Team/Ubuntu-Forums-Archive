---
title: "Can't Boot Windows from Grub"
date: 2020-02-02
forum: General Help
---

### Post by binu95 on 2020-02-02
I'm not super savvy, but I've been dual booting my laptop and had a friend install it for me. As I saw the PC slowing down, so I reset the PC to only have Windows and then proceeded to clone the HDD to a new SSD. Cloning went fine and Windows booted up on the new SSD alright, but now I had a work buddy try and install Ubuntu on top of this. Now Ubuntu boots up fine from Grub, but while trying to boot Windows, I'm shown "*error: disk ` (hd0,4)` not found.*"

In Ubuntu explorer, I can see the Windows Partition like so

 [IMG]https://imgur.com/a/FKdvVzI[/IMG][IMG]https://imgur.com/YTsrTnf[/IMG][IMG]https://i.imgur.com/YTsrTnf.jpg[/IMG]

And When opened, it does show the files within(*I know it isn't supposed to*)

[IMG]https://i.imgur.com/hrNw5Hy.png[/IMG]


How do I fix this, to be able to get back to booting both Ubuntu & Windows? The copy of Windows is genuine and came bundled with the PC.

---

### Post by coffeecat on 2020-02-02
Not a tutorial.

*Thread moved to **General Help**.*

---

### Post by CelticWarrior on 2020-02-02
Try this steps:

[LIST=1]
[*]In Windows, disable **Fast Startup**.
[*]Boot Ubuntu, open Terminal, and run ```
sudo update-grub
```
[/LIST]

---

### Post by yancek on 2020-02-02
If the update-grub doesn't produce a bootable windows, you should go to the site below while booted into Ubuntu and download and run boot repair to get more information to post here.  Make sure you use the 2nd option described on the page using the ppa.  When you run it, make certain you select the Create BootInfo Summary option and do NOT try to make any repairs.  When it finishes, you should get a link to post here which will give details on your system and someone should be able to help.  I'd be surprised if the windows boot files were on sda4 but I guess it's possible although what you report above would indicate that partition does not exist.

---

### Post by binu95 on 2020-02-02
@yancek Tried update-grub, didn't work. Also, can't seem to be able to find the website you're talking about. Can you post it again?

---

### Post by CelticWarrior on 2020-02-02
Here's the site [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and I reiterate the advice to use the 2nd option and do NOT try to make any repairs. What we need is the information from "Create BootInfo Summary". And this is just to confirm what everybody is suspecting already.

---

### Post by binu95 on 2020-02-02
Here's the Boot Info Summary - [http://paste.ubuntu.com/p/CW4mwFCGJ9/](http://paste.ubuntu.com/p/CW4mwFCGJ9/)

---

### Post by oldfred on 2020-02-02
Not exactly sure how you got to this.

I looks like you have overwritten the required UEFI boot partition ESP - efi system partition with swap.
And installed Ubuntu in BIOS boot mode, to an UEFI/gpt partitioned drive. 

If you restore the ESP, and reinstall both Windows UEFI boot files & Ubuntu's UEFI version of grub you should be able to repair system.

First use gparted from Ubuntu live installer and change sda2 back to FAT32 and add boot & esp flags.
Not sure if any files will still be there or not.

Then using live installer, make sure you boot in UEFI boot mode and add Boot-Repair. 
Using its advanced options choose the total reinstall of grub & latest kernel.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Then you will need to use your Windows repair flash drive to run a complete set of Windows repairs to reinstall its UEFI boot.

---

### Post by CelticWarrior on 2020-02-02
@oldfred

According to the OP, Windows (and at that point only Windows) was cloned from another driver and supposedly worked just like that. Then a friend installed Ubuntu.

---

### Post by yancek on 2020-02-02
As pointed out by oldfred in the post above, your 'buddy' installed Ubuntu incorrectly.  The hard drive is GPT which means that if window was installed there by the manufacturer, it was a UEFI install.  As stated above, you have no EFI partition which you will need.  If you want to boot windows.  THis is the primary reason your windows system no longer boots.  You can see in the boot repair output (line 509) where the error you report comes from.  There is an entry there for windows but it is not a correct EFI entry and will not work.  That line on a proper grub EFI install should be something like below:

```
chainloader /EFI/Microsoft/Boot/bootmgfw.efi 
```

The link below describes dual booting windows 10 and Ubuntu UEFFI.  Worth a read so you have some understanding of it.  A Linux install on a GPT drive using Legacy boot (Grub in the MBR) generally requires a 1-2MB bios_grub partition which I see no sign of.  Not sure how Ubuntu even boots?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

One thing you might try is to turn swap off on your system using:  sudo swapoff -a then create a mount point for sda2 and mount it to see if there are any files there.  I doubt it, but worth a try as it won't harm the system and you can simply turn it back on.  Incidentally, newer Ubuntu releases don't use a swap partition but rather a swap file.

Following the instructions by oldfred again to repair Ubuntu will be a step but there is no way to repair the damaged windows files from Ubuntu or any other Linux.

---

