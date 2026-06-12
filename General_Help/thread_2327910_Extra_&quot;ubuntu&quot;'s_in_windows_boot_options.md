---
title: "Extra &quot;ubuntu&quot;'s in windows boot options menu with every boot"
date: 2016-06-15
forum: General Help
---

### Post by jed5 on 2016-06-15
This might be related to the problem I was having with grub: [URL="http://ubuntuforums.org/showthread.php?t=2327695"]link
[/URL]
Computer: HP dv6t-7000 laptop, 500gb ssd, Windows 8.1 installed first, dual booting Ubuntu 16.04

From what I've gathered, some HP computers' UEFI does not conform to the standard, making it difficult to load grub automatically. There are some manual fixes for this, but until I try those, using the Boot Options Menu (F9 on startup) works. However, every time I boot up Ubuntu, an extra "Ubuntu" entry is added to the Boot Options Menu. I can delete the extra entries using bcdedit in windows (and probably efibootmgr in linux), but that's a pain. Anyone know how to stop the additional Ubuntu entries?

---

### Post by ckotichas on 2016-06-15
In case the extra entries are due to old installations, try running:
```
update-grub
```

If there are still more entries that you don't like, go through /boot/grub/grub.cfg and remove the menuentry and/or submenu blocks that you don't like.

---

### Post by Bucky Ball on 2016-06-15
Keep the entry for recovery in the second screen if its there. Should be under the first Ubuntu entry. You may need that. It is a good idea to leave two kernels in grub. If one fails, you have the other to fall back on (and this has come in handy plenty of times here!).  

Without more info about how you have these installed, hard to say, but is this correct? You're booting to a Windows boot menu, choosing Ubuntu, and that is taking you to the grub menu? You want straight to the grub menu?

* PS: Just saw last post. 

```
sudo apt-get autoremove
```

... should kill dead kernels, leaving the present and previous one. ;)

Also, please post output, between code tags, of 

```
sudo blkid
```

---

### Post by oldfred on 2016-06-15
Are the extra entries in the UEFI boot menu or grub boot menu?

If UEFI, having two is normal. One is shim and the other grub. But shim should work whether UEFI Secure boot is on or not.
Some UEFI find all the files/folders with .efi files in /EFI and add them to UEFI boot menu.

post this:
sudo efibootmgr -v

If from grub, post this:
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by ckotichas on 2016-06-21
Jed5, don't forget to mark this thread as "SOLVED" if your issue was resolved.

---

### Post by jed5 on 2016-06-21
Sorry. I don't think I was clear enough. 

The extra entries are in the UEFI boot menu. Everytime I boot ubuntu, another one shows up. I can remove them manually, but I'd like to stop them from showing up.

---

### Post by jed5 on 2016-06-21
Here's the output of efibootmgr -v:

```

BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 3002,3000,3001,3003,3004,3005,2001,2002,2003
Boot0000* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0001* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* Windows Boot Manager    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot0003* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0004* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0005* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3000* Internal Hard Disk or Solid State Disk    RC
Boot3001* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC
Boot3004* Internal Hard Disk or Solid State Disk    RC
Boot3005* Internal Hard Disk or Solid State Disk    RC

```

---

### Post by oldfred on 2016-06-21
I would try deleting with efibootmgr.
But Something strange is happening if UEFI is adding them. Are you sure it is not Windows BCD adding them?
As I understand it, BCD will resync with UEFI. So you may have to delete in both places to prevent each from updating the other.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by jed5 on 2016-06-21
I tried deleting extra entries using that method. They do go away. However, another "Ubuntu" appears in the windows boot options menu every time I boot Windows. Booting Ubuntu doesn't add an additional entry, but booting Windows does. So I'm guess its a Windows problem. 

I tried running boot repair again, but it doesn't stop the additional "Ubuntu"'s from appearing.

What did you mean by "delete in both places to prevent each from updating the other"? 

Thanks!

---

### Post by oldfred on 2016-06-21
Delete in BCD and UEFI at same time.

But if BCD keeps adding new entry that is strange.

[https://technet.microsoft.com/en-us/library/cc749510(v=ws.10).aspx](https://technet.microsoft.com/en-us/library/cc749510(v=ws.10).aspx)

---

### Post by jed5 on 2016-06-21
A little more information/summary: I can boot from any of the "Ubuntu" or "ubuntu" 's in the UEFI boot options menu (accessed with F9 at startup). They all open grub, from which I have about 8 or so options, 1 of which is "*Ubuntu" and another is "Windows Boot Manager". Selecting the former boots Ubuntu, selecting the latter boots Windows. If I don't hit F9 at startup, it automatically boots into Windows. Every time I boot Windows, an extra "Ubuntu" is added to the UEFI boot options menu.

Here's what the boot options menu looks like:
[ATTACH=CONFIG]269704[/ATTACH]

Here's what grub looks like:
[ATTACH=CONFIG]269703[/ATTACH]

I tried deleting extra Ubuntu entries (left "ubuntu" and 1 "Ubuntu") in Windows with bcdedit, shutdown windows, then went into the boot options menu only to find an additional "Ubuntu" entry. Not sure when it is getting added. 

Here is current output of efibootmgr -v:
```

BootCurrent: 003D
Timeout: 0 seconds
BootOrder: 300D,3005,3008,300A,2001,2002,2003
Boot0005* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0008* ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
Boot000A* Ubuntu    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot000D* Windows Boot Manager    HD(2,GPT,afc79a47-1095-412f-981a-8d1184497e26,0x96800,0x32000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot3005* Internal Hard Disk or Solid State Disk    RC
Boot3008* Internal Hard Disk or Solid State Disk    RC
Boot300A* Internal Hard Disk or Solid State Disk    RC
Boot300D* Internal Hard Disk or Solid State Disk    RC

```

The "internal hard drive or solid state disk" entries do not show up in the UEFI boot options menu. Not sure what they are.

---

### Post by oldfred on 2016-06-21
You have two entries with capital Ubuntu, the entry normally created is ubuntu.
Is the entry created the one's with capital U?
And two entries is normal, as you have both grubx64.efi and shimx64.efi.

If you boot the entry "Boot from efi file" what boots? That may be the Internal hard disk entry. which should be /EFI/Boot/bootx64.efi which is a fallback or hard drive entry.
But bootx64.efi is normally a copy of Windows .efi file, but Boot-Repair can back that up and make it be shimx64.efi to boot Ubuntu/grub from a default entry.
And then based on what Boot from efi file gives you can you see size of bootx64.efi  and tell if same as /EFI/ubuntu/shimx64.efi or Windows /EFI/Microsoft/Boot/bootmgfw.efi?

---

### Post by jed5 on 2016-06-22
Extra capital U "Ubuntu"'s are added every time I boot Windows. According to bcdedit, the shimx64.efi is the lower case "ubuntu" and the grubx64.efi is the "Ubuntu" (different entries, but all point to same grubx64.efi). 

If I boot from efi file in the UEFI boot options, I can go through a series of menus and boot either grub or Windows. 

Sorry, I don't understand exactly what you want me to do in your last paragraph. Where is the bootx64.efi file?

---

### Post by oldfred on 2016-06-22
The /EFI/Boot/bootx64.efi is the fallback or hard drive entry. I believe it then is your boot from efi file entry. I think then you get either the grub menu or the BCD menu in Windows and it reboots back to ubuntu and grub menu.
If bootx64.efi is Windows file that boots BCD, if it is grub or shim it boots to grub menu.
You need to look in your ESP to see size of bootx64.efi to see which it is now.
In Ubuntu. If you have not run Boot-Repair the ESP is locked.
ls -l /boot/efi/EFI/ubuntu/*
-rwxr-xr-x 1 root root 1067896 Apr 17 14:46 /boot/efi/EFI/ubuntu/grubx64.efi
-rwxr-xr-x 1 root root 1289424 Apr 17 14:46 /boot/efi/EFI/ubuntu/shimx64.efi
I only have Ubuntu so do not have these. If not shown check case or path.
ls -l /boot/efi/Boot/*
ls -l /boot/efi/Microsoft/Boot/bootmgfw.efi 

I would like to make bootx64.efi the shimx64.efi file and see if you can set that as a default UEFI boot entry. And then remove both ubuntu & Ubuntu entries from BCD.

       
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI. 
 	'Use the standard EFI file' in advanced options. 

So run Boot-Repair's advanced options & tick/check the 'Use the standard EFI file'. Then see if grub menu directly appears on efi file boot.
Or you can manually backup bootx64.efi and copy shimx64.efi to be bootx64.efi. Details in link in my signature and most of the HP threads posted.

---

### Post by jed5 on 2016-06-24
Ok, in my /EFI/Boot directory, I have two files: bkpbootx64.efi and bootx64.efi. In my /EFI/ubuntu directory, I have 5 files, two of which are grubx64.efi and shimx64.efi. shimx64.efi and bootx64.efi are the same size, so I'm guessing they are the same file. 

I will try deleting all "Ubuntu" and "ubuntu" entries. 

A related concern: If you look in post 11, you can see an output of my efibootmgr. The number of "Internal Hard Disk or Solid State Disk" are growing with the extra Ubuntu's. Not sure why.

---

### Post by jed5 on 2016-06-24
I deleted all "ubuntu" and "Ubuntu"'s, and deleted all but one of the "Internal Hard Disk or Solid State Disk" entries using efibootmgr. I then restarted, booted into windows, restarted, booted with f9-> efi file->drive->ubuntu->grub. Running efibootmgr shows 2 "Ubuntu" entries and 3 "Internal Hard Disk or Solid State Disk" entries. Something is adding a new entry with every boot or shutdown. Very odd.

---

### Post by oldfred on 2016-06-24
Do not know BCD, but do you have entries in BCD?
Windows syncs BCD & NVRAM, so it may be adding entries back?

---

### Post by jed5 on 2016-06-24
Here is the result of "bcdedit /enum firmware":
```

C:\Windows\system32>bcdedit /enum firmware


Firmware Boot Manager
---------------------
identifier              {fwbootmgr}
displayorder            {bootmgr}
                        {2bd8007e-38fb-11e6-8292-806e6f6e6963}
                        {2bd8007f-38fb-11e6-8292-806e6f6e6963}
                        {a67654aa-3a70-11e6-8296-806e6f6e6963}
                        {da695b5b-383c-11e6-8291-806e6f6e6963}
                        {da695b5c-383c-11e6-8291-806e6f6e6963}
timeout                 0


Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\ubuntu\grubx64.efi
description             Windows Boot Manager
locale                  en-US
inherit                 {globalsettings}
integrityservices       Enable
default                 {current}
resumeobject            {2f068155-49c8-11e5-9168-b87bd413f1c0}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30


Firmware Application (101fffff)
-------------------------------
identifier              {2bd8007c-38fb-11e6-8292-806e6f6e6963}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\Microsoft\Boot\bootmgfw.efi
description             Windows Boot Manager


Firmware Application (101fffff)
-------------------------------
identifier              {2bd8007d-38fb-11e6-8292-806e6f6e6963}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\ubuntu\grubx64.efi
description             Ubuntu


Firmware Application (101fffff)
-------------------------------
identifier              {2bd8007e-38fb-11e6-8292-806e6f6e6963}
description             Internal Hard Disk or Solid State Disk


Firmware Application (101fffff)
-------------------------------
identifier              {2bd8007f-38fb-11e6-8292-806e6f6e6963}
description             Internal Hard Disk or Solid State Disk


Firmware Application (101fffff)
-------------------------------
identifier              {a67654a9-3a70-11e6-8296-806e6f6e6963}
device                  partition=\Device\HarddiskVolume2
path                    \EFI\ubuntu\grubx64.efi
description             Ubuntu


Firmware Application (101fffff)
-------------------------------
identifier              {a67654aa-3a70-11e6-8296-806e6f6e6963}
description             Internal Hard Disk or Solid State Disk


Firmware Application (101fffff)
-------------------------------
identifier              {da695b5b-383c-11e6-8291-806e6f6e6963}
description             USB Drive (UEFI)


Firmware Application (101fffff)
-------------------------------
identifier              {da695b5c-383c-11e6-8291-806e6f6e6963}
description             Internal CD/DVD ROM Drive (UEFI)

```

Looks similar to output of efibootmgr. What I find interesting is that the "Windows Boot Manager" now points to grub, but the computer still boots straight into windows (I think that's related to [my other post]("http://ubuntuforums.org/showthread.php?t=2327695")). I don't see the bootx64.efi or shimx64.efi files in that list, though.

---

### Post by oldfred on 2016-06-24
Ubuntu uses the UUID, UEFI uses the GUID(gpt) and I have no idea what Windows is using, but those look like they could be the source of multiple entries.

But I do not know how to clean up BCD. I would be sure to make a backup.
And then If a Windows site explains BCD more, delete extra entries at same time you delete from UEFI.

 Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

---

### Post by jed5 on 2016-06-24
I've tried that before. That's how I remove entries with bcdedit. I can do that, and it works, but the entries come back every time I reboot (+1 "Ubuntu" entry per reboot). It's like there's a file somewhere that is saying "add an extra Ubuntu entry to the boot menu every time I boot Windows".

---

### Post by oldfred on 2016-06-24
Order of deletion may make a difference, but I do not see how if you delete from both BCD and then from NVRAM, they can reappear.

One or the other must keep updating. I do not think there is any third place where it can copy entries from.

I might try deleting from BCD with a Windows repair CD, so you are not in Windows.
And delete from NVRAM with efibootmgr from live installer.

You have have one of these anyway:
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

