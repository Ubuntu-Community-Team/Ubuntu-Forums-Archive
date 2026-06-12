---
title: "Error 1962 Lenovo Booting Problem"
date: 2020-01-26
forum: General Help
---

### Post by msroj88 on 2020-01-26
Hello!
Trying to re-install a new OS on my old PC. Used to be Windows but cleaned out the HDD and trying to install Ubuntu 18.04.
Got stuck with the Error 1962. No operating system found.

Googled about this, changed settings in the BIOS and created the boot for Microsoft too.
But still the same error. 

Can anyone help me find a solution?
What more info do you need from me?

[http://paste.ubuntu.com/p/bg42vFXQSf/](http://paste.ubuntu.com/p/bg42vFXQSf/)

---

### Post by oldfred on 2020-01-26
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files (uses fallback boot of drive)
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

It says Secure Boot may be on. Have you tried with UEFI Secure Boot off.

Some vendors violate UEFI standards and have UEFI that only boots by description and that description has to be "Windows Boot Manager". Usually users are dual booting and there is a fallback or hard drive boot entry in UEFI at /EFI/Boot/bootx64.efi. This is the same type of entry used to boot external drives.

You show two Hard Drive entries. Do either of those work?

If only booting Ubuntu you can create a new UEFI boot entry that has Windows description but boots Ubuntu.

See this for details:
man efibootmgr

Standard Ubuntu entry:
sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Ubuntu" -d /dev/sdX -p Y
sdX is drive, Y is efi partition default is sda and first partition, so only required if not sda1

Use Windows description and since efibootmgr defaults to sda1, you do not need those parameters.
sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Windows Boot Manager" 
Fall back entry:
sudo efibootmgr -c  -l \EFI\Boot\bootx64.efi -L "Hard Drive"

Your UEFI boot menu will just show description, to see details & confirm your new entries:
sudo efibootmgr -v

You can remove duplicate or non-working entries in UEFI.
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

---

### Post by msroj88 on 2020-01-26
Thanks for your answer, oldfred.
Read your solved-post before I ended up here.

Can’t find the secure boot-option in the Lenovo BIOS.

I got two hard drives, the 30gb one is a USB with the Ubuntu. The 250gb one got three partitions. 

/dev/sda1 - EFI
/dev/sda2 - Swap
/dev/sda3 - Ext4

Changed the boot entries and did not help. 

I find it strange that the Ubuntu-USB boots without any problems as long as it boots first. But i get the error 1962 on the main hard drive even though Ubuntu is there. Bad installation by me?

---

### Post by oldfred on 2020-01-26
Is this only an Ubuntu install?

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by msroj88 on 2020-01-27
Is it supposed to this hard to install Ubuntu? Will it even be possible?
I&#8217;m about to give up and buying a brand new PC.

Pastebin #1 - paste.ubuntu.com/p/Z8QMP3BxmJ
Pastebin #2 - [http://paste.ubuntu.com/p/tBSPwZFmPy/](http://paste.ubuntu.com/p/tBSPwZFmPy/)

Formating the HDD right now.
There is no operating system avaible at all, expect Ubuntu on the USB.
There is no Secure Boot-option in the BIOS.

I have done A, C in your post about &#8220; Systems that only boot Windows from UEFI.&#8221;, since there was a few cases that solved it through those options. But I questioning myself if I did option A all the way.

Tell me, in want order should I do now this to get this going properly?

Second option in the installer?

---

### Post by oldfred on 2020-01-27
Edited second link to be clickable.

Not related, but never seen this error before:
> ** Warning ** : Boot000a is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.

I would just remove 000a
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Install looks normal. I would think then issue is Lenovo. Have you updated UEFI to latest available? That can fix a lot of issues, not always listed in fixes they claim to be fixing. Since no Windows you typically have to download update & save to a FAT32 formatted drive or partition. (I use my ESP.) And then from within UEFI you can read the update file.

Have you tried booting Windows entry. second hard drive entry, or ubuntu entry. 
And do you get same error on all of them?

Microsoft requires vendors to have UEFI Secure Boot and allow users to turn it off. Probably because many were installing Windows 7 and 7 does not support UEFI Secure Boot. May be called Windows or "Other". My system says in fine print somewhere to use "Other" if installing Windows 7. Some other systems have it in combination with other settings or behind setting your own UEFI password. (never lose UEFI password, if you set it or reset to blank when done).

I build my own desktop systems, using parts that are not bleeding edge but fairly new. And have not had many issues.

---

### Post by msroj88 on 2020-01-28
Before i begun to format the HDD, I actually checked boomgr and none had 000a, all were numbers.

By updating UEFI, you mean updating the BIOS? How?

I have went through the whole BIOS, no luck with Secure Boot. Will try again.

I one of the solved-posts, it said to add “Ubuntu”, “Windows Boot Manager” and “Hard Drive”. Didn’t help, but no sure if they were in the right order and I did not try “UEFI Hard Drive”.

Will give it another try with a fresh install.

---

### Post by msroj88 on 2020-01-28
My BIOS-version is called 9HKT43AUS.
Googled it, did what they wanted me to do for Secure Boot-off, didnt help.

Boot000a is the real hard drive. Tried to remove it, but every reboot it gets added again.
Re-did the bootorder, didnt help.

So, tell me. Im giving this one more try before i give up.
Any suggestions.....

> ** Warning ** : Boot000a is not UEFI Spec compliant (lowercase hex in name)
** Warning ** : please recreate these using efibootmgr to remove this warning.
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0005,0001,000A,0000,0007,0008,0009
Boot0000* ubuntu
Boot0001* CD/DVD Drive
Boot0002* Hard Drive
Boot0005* Network Card
Boot0007* Windows Boot Manager
Boot0008* Hard Drive
Boot0009* UEFI: hp v221w 1100
Boot000a* Hard Drive


Clean boot

> BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0002,0001,0000,0009
Boot0000* Windows Boot Manager    HD(1,GPT,b15927fc-88cd-4369-bdef-60aaecbd5e3e,0x800,0x1dc800)/File(EFIubuntushimx64.efi)
Boot0001* Hard Drive    HD(1,GPT,b15927fc-88cd-4369-bdef-60aaecbd5e3e,0x800,0x1dc800)/File(EFIBootbootx64.efi)
Boot0002* UEFI Hard drive    HD(1,GPT,b15927fc-88cd-4369-bdef-60aaecbd5e3e,0x800,0x1dc800)/File(\EFI\Boot\bootx64.efi)
Boot0009* UEFI: hp v221w 1100    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(4,0)/HD(1,MBR,0xe419e5e,0x800,0x3bee700)


---

### Post by oldfred on 2020-01-28
Your 0000 Windows Boot Manager has () in it, that does not look right.
I would remove 0000 and create a new one.  See post #2.

sudo efibootmgr -c  -l \EFI\ubuntu\shimx64.efi -L "Windows Boot Manager"

It looks like Lenovo offers ISO update files in addition to the Windows .exe files. 
So you can download ISO and create a live installer of it to boot & update UEFI.

---

### Post by msroj88 on 2020-01-29
I really do appreciate your help, oldfred.

You mind telling me how make a installer of the Update-BIOS?

Downloaded the file for USB-updating and extracted the files directly to the USB and set it as primary boot, nothing happend.

---

### Post by oldfred on 2020-01-29
Most UEFI can directly read a FAT32 formatted partition or external device's partition.
And then it directly loads the update file.
You can check your vendor's manual for your sytem. It should be on-line in same support area as UEFI/BIOS updates. All the other drivers are just for Windows.

Both my Asus and Gigabyte motherboards read FAT32 and I save update file into my ESP - efi system partition. I did have make it a bit larger and change default permissions in fstab, so I could directly write into it. But have used a FAT32 flash drive in the past.

Some have a downloadable ISO that creates a old DOS bootable flash drive that can run update.

And a few now can update directly from Linux. Says Lenovo added a lot of files, but probably just newer systems.
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by msroj88 on 2020-02-01
Like i said before, really appreciate your help. But I’m giving up, this way too much work to get it going. I’ll just pay for a working copy of Windows.

Thanks either way, oldfred.

---

