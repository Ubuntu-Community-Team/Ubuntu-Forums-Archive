---
title: "Lost Windows 10 option in GRUB"
date: 2016-09-03
forum: General Help
---

### Post by kingamongthepigs on 2016-09-03
Hi, I just installed Ubuntu yesterday alongside pre-existing windows 10(BIOS) and all is well. However, after today and an Ubuntu update, the Windows 10 option is no longer available in Grub.
I tried boot-repair, which didn't solve the problem. There's also no option in the BIOS to fix the problem.
Here are my logs from boot repair
[URL="http://paste2.org/Bke43cZy"]http://paste2.org/Bke43cZy
[/URL]
Thanks in advance! :)

---

### Post by jarvis3 on 2016-09-03
Id try turning on your computer and hitting f12. this will give you options of what you could boot. for windows boot: windows boot manager for booting ubuntu boot: ubuntu. if you have the error { Grub rescue } id hit f2 and start a diagnosis. Good luck! I HATE GRUB RESCUE

---

### Post by kingamongthepigs on 2016-09-03
Thanks a lot for your help! The only options available was booting from Hard Disk or EFI. The Hard Disk option go straight to Grub with only Ubuntu and EFI doesn't do anything. 
Here's my bootinfoscript result:

[http://pastebin.com/NgAvmLqJ](http://pastebin.com/NgAvmLqJ)

---

### Post by yancek on 2016-09-03
The information you posted shows you have Grub installed in the MBR and that you have four windows partitions and one Linux partition which is almost at the end of the drive.  Not sure if that is related, I doubt it but it is also generally a good idea to have boot files near the beginning of the drive.

You do not have an EFI partition so that means you are using the older MBR system.  You don't have any entry for any windows system on any of the partitions in the grub.cfg file for Ubuntu so the first thing I would suggest is when you aree booted into Ubuntu to run from a terminal:  sudo update-grub   Watch the output for a windows entry.

Did you install a newer windows over earlier versions?  I see a boot.ini file on sda2 which hasn't been used with a bootloader since xp.

---

### Post by kingamongthepigs on 2016-09-03
I used to auto partition option when installing ubuntu alongside windows. Maybe that's what caused the problems.
I think my partitions might have been messed up. Here's how they look like right now:

[IMG]http://i196.photobucket.com/albums/aa124/king_amongthepigs/Screenshot%20from%202016-09-04%2005-34-12_zpsyupt093g.png[/IMG]



I'm on Windows 10 Pro, installed on the 120GB Partition. I did reinstall and upgrade my windows several times in the past. The Windows version was never older than 7 though.

Here's the result for grub:

[IMG]http://i196.photobucket.com/albums/aa124/king_amongthepigs/Screenshot%20from%202016-09-04%2005-45-21_zpstzb7ft63.png[/IMG]

---

### Post by yancek on 2016-09-03
So what happened when you ran sudo update-grub?

I see you have RAID which I have never used so I don't what impact if any that might have.

---

### Post by mook765 on 2016-09-04
Your boot-repair summary shows three different versions of Windows installed.
Win10 seems to be installed on sda5 which is a logical partition. Strange is that you have a boot-flag on this partition, normally a boot-flag can only exist on a primary partition.
I think that windows did some tricks with LVM (Logical Volume Manager) to achieve this. In the header of this partition sda5 it also says, that the partition starts at sector 2048, what is not real, because on sector 2048 is start of sda1. Grub is not able to manage partitions which are managed by Windows LVM. I think that is the reason for the missing menu-entry in Grub.
Difficult to give good advice in this case.
If you don't use older Windows versions, maybe clean up your drive, make new partitions, install one version of Windows and then Ubuntu.
Another thing:
You only made a boot-summary-report, no repair.
In the report it show us what is recommended repair. If you run boot-repair again and use option recommended repair, you might be able to boot into Ubuntu or Win7.
Try that if you need your computer for some urgent work...

---

### Post by kingamongthepigs on 2016-09-04
I ran boot repair again and here's the report:
[http://paste2.org/f0BOXw7p](http://paste2.org/f0BOXw7p)

Here's the result when I ran sudo update-grub:
> Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found Windows Recovery Environment (loader) on /dev/sdc1


So far I still can't see Windows in Grub. At this point I think I should just reinstall Windows 10. I'm not sure that changes I need to make to the partitions to ensure a more stable environment though.

---

### Post by mook765 on 2016-09-04
You can boot to Windows Recovery Environment and from there repair windows startup.

---

### Post by kingamongthepigs on 2016-09-04
I have tried that and sadly, it says windows startup cant be repaired. I also did chkdsk before hand.

---

### Post by westie457 on 2016-09-04
This from your first Boot Report.> 
[LIST=|INDENT=1]
[*][FONT=inherit][COLOR=#666666][FONT=inherit]===================[/FONT][/COLOR] parted -lm:[/FONT]
[*]
[*][FONT=inherit]BYT[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]/dev/sda:1000GB:scsi:512:4096:msdos:ATA ST1000LM024 HN-M:[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]1:1049kB:106MB:105MB:ntfs::[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]2:109MB:130GB:130GB:ntfs::[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]3:130GB:560GB:429GB:ntfs::[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]4:560GB:1000GB:440GB:::lba[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]5:560GB:957GB:397GB:ntfs::boot[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]6:957GB:992GB:34.5GB:ext4::[FONT=inherit];[/FONT][/FONT]
[*][FONT=inherit]7:992GB:1000GB:8479MB:linux-swap[COLOR=#666666][FONT=inherit]([/FONT][/COLOR]v1[COLOR=#666666][FONT=inherit])[/FONT][/COLOR]::[FONT=inherit];[/FONT][/FONT]
[/LIST]
Shows the Boot flag on an extended partition, it should be on the first primary partition or most possibly on the second partition

Use Gparted to change the flags then try a ```
sudo update-grub
```

---

### Post by Jimysbil on 2016-09-04
According to your partition table your Windows bootable partition should be /dev/sda1 and your Windows partition /dev/sda2.So Grub should be able to find Windows on sda1.If you can mount that partition on linux and there is a bootmgr on the root of your partition you should be ok.
In any case I would suggest you run a chkdsk from a windows dvd/usb or (from ubuntu) the command:
```
sudo ntfsfix /dev/sda1
```

If that doesn't work you could try to reinstall your Windows Systems Reserved partition boot record.Boot from a Windows CD/USB and press SHIFT+F10 to open a cmd prompt.Type the commands:
```
diskpart
list volume [COLOR="#FF0000"]--> It will print all your volumes and mount points.[/COLOR]
```
If your partition is not mounted try this:
```
list disk [COLOR="#FF0000"]--> It will print all your disks with a number.[/COLOR]
select disk [COLOR="#FF8C00"]{number of the disk}[/COLOR]
list partition [COLOR="#FF0000"]--> It will print every partition on your selected disk with a number.[/COLOR]
select partition [COLOR="#FF8C00"]{number of partition}[/COLOR]
assign letter=[COLOR="#FF8C00"]{any not already used letter}[/COLOR]
active --> [COLOR="#FF0000"]In case you want to set this partition as active.[/COLOR]
quit
```
When you finish with diskpart type the commands:
```
cd X:\boot\
bootsect /nt60 [COLOR="#FF8C00"]{the letter you chose before}[/COLOR]
exit
```

After that you can boot Ubuntu and type on a root terminal:
```
update-grub
```

---

### Post by mook765 on 2016-09-04
I am sad too, 
your system looks a bit weird and it might be better to take a broom and sweep (fresh install of Windows first, then Ubuntu).
If your machine has UEFI-capabilities you may want to change to UEFI. UEFI uses GPT-partitions, this is a bit different from old MBR-partitions and you wouldn't have to think about logical partitions anymore.
If you have older machine with old BIOS, you have to stay with MBR-partitions.
Here you can find a lot of information about installing in UEFI-mode:
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by kingamongthepigs on 2016-09-04
I've tried everyone's suggestion and nothing have been working so far :( I will be reinstalling Windows and Ubuntu I guess. Is there anything I should do to make sure things will stay in place when I do so?
My computer does indeed have UEFI-capabilities but I didn't install UEFI. I will after being able to access to Windows, maybe through a OS reinstall.

---

