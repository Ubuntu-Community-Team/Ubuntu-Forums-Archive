---
title: "Ubuntu not booting after system update but....."
date: 2014-06-24
forum: General Help
---

### Post by behanj on 2014-06-24
The massive but! - It will boot with a Ubuntu CD in the drive, but boots to the regular install of Ubuntu not the Live CD.

Very weird, I'm dual booting Windows 8 and Ubuntu 12.04 on an Asus X550C

Last night several updates ran and upon rebooting Ubuntu gets to just past the Grub loader and stops there, on the dark red screen but before the Ubuntu name is shown.

I tried Boot Repair and it hasn't worked for me.

I tried going into the computer Bios to set booting to CD but it's not an option in the boot menu anymore.

Boot Repair put this up - [http://paste.ubuntu.com/7694285/]("http://paste.ubuntu.com/7694285/")

I checked GParted after reading this

> The boot files of [The OS now in use - Ubuntu 12.04.4 LTS] are far from the start of the >disk. Your BIOS may not detect them. You may want to retry after creating a /boot >partition (EXT4, >200MB, start of the disk). This can be performed via tools such as >gParted. Then select this partition via the [Separate /boot partition:] option of [Boot >Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

But it shows the boot partition at the start of the disk.

Any help would be massively appreciated

---

### Post by oldfred on 2014-06-24
Ignore the far from start of disk error. I have yet to see a UEFI system need any changes. It does apply to some older BIOS and a few more older BIOS with an install on a larger USB hard disk.

It looks like you have done several 'fixes'?
You show this:
      ```
 BootOrder: 0001,0002,0004,0003
Boot0001* ubuntu	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIubuntu[COLOR=#ff0000]shim[/COLOR]x64.efi)
Boot0002* ubuntu	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIUbuntu[COLOR=#ff0000]grub[/COLOR]x64.efi)
Boot0003* Windows Boot Manager	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIubuntu[COLOR=#ff0000]grubx64.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Windows Boot Manager	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIMicrosoftBoot[COLOR=#ff0000]bootmgfw.efi[/COLOR])


```    

And in efi partition:
                        /EFI/Microsoft/Boot/[COLOR=#ff0000]bkp[/COLOR]bootmgfw.efi 
                       /EFI/Microsoft/Boot/bootmgfw.efi 

It looks like you have renamed the shim file to have a Windows name in UEFI in 0003.
And Boot-Repair has renamed the Windows boot file from bootmgfw.efi to bkpbootmgfw.efi. With that change you choose Windows in UEFI menu and it boots grub. And then you can only boot Windows from grub menu by choosing the bkpbootmgfw.efi which is really the original Windows file.

Is your system one that only boots Windows? Or you cannot choose the Ubuntu entry. If you have secure boot on only the shim version will work or if secure boot is off either shim or grub should work. But if vendor modified UEFI then only entries with Windows Boot in UEFI will let you boot any UEFI system.

I would undo the rename that Boot-Repair did:

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.


Some prefer to rename this file and choose to boot hard drive. You copy shim into /efi/boot and rename shim to be this:

 /EFI/BOOT/BOOTX64.EFI

Others do like rEFInd.
      
 [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by behanj on 2014-06-25
Hi, Thanks for the reply

To describe the problem a little better -
Windows boots without a problem when selected in Grub
Ubuntu won't boot unless there's an Ubuntu CD in the drive. Then it boots to my HD installed, regular, version of Ubuntu, not the Live CD version.

How could the CD being present affect the bootup of Ubuntu?
Are there files on there that I could copy to my HD to fix my boot issues?

I ran the Boot Repair again with the option to Restore EFI Backups enabled, the result looks and acts the same as before.
Here is the log - [http://paste.ubuntu.com/7700031/]("http://paste.ubuntu.com/7700031/")

Thanks again for your reply, and sorry for not getting back sooner, I'm based in Bangkok so time difference may be an issue.

---

### Post by behanj on 2014-06-29
Hi guys,

I'm going to go ahead and try a few of the Advanced options in Boot Repair

The Purge Grub before Reinstall and Purge Kernel options look tempting.

Is this a good idea? I can't really be without my machine and re setting up everything is going to be a pain but it looks like that might be the only option.

Any feedback would be appreciated.

Thanks,
John

---

### Post by oldfred on 2014-06-29
What computer?
Are you booting Ubuntu entry, Windows entry that is grub or 2nd Windows entry that is really Windows?

```
 BootOrder: 0000,0004,0003
Boot0000* ubuntu	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0003* Windows Boot Manager	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIubuntu[COLOR=#ff0000]grubx64.efi[/COLOR])WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0004* Windows Boot Manager	HD(1,800,32000,4600d0bb-52a4-49a1-b258-445f5ac10fe2)File(EFIMicrosoft[COLOR=#ff0000]Bootbootmgfw.efi[/COLOR])


```

And do you have secure boot on or off? grub entry only works with secure boot off. Shim should work with secure boot on or off.

---

### Post by behanj on 2014-06-29
Hi,

Thanks for the reply.

Secure boot is disabled.
I can boot to Ubuntu, so long as an Ubuntu CD is in the drive. It boots to my HD install of Ubutu but for some reason needs the CD. This is the problem I am trying to resolve.
Windows boots with the grub entry but not with the second entry.

Thanks again,
John

---

### Post by oldfred on 2014-06-29
Does Ubuntu entry in UEFI work or only the Windows named entry that is really grub.

Some (many) computers have modified UEFI to only boot a Windows entry.

---

### Post by behanj on 2014-06-30
Hi,

Thanks again for replying.

I think I know what you mean - can Ubuntu be booted straight from the Bios rather than Grub, is that right?
I've taken a few photos of the Grub screen and Bios that might be helpful.

This is what I see on Grub -
[IMG]https://lh4.googleusercontent.com/-0tcCUjL8Nek/U7Ey0LAVkcI/AAAAAAAAGh0/JGTd5zjrJc8/w640-h480-no/20140630_165001.jpg[/IMG]

Here is the boot order screen of my Bios - 
[IMG]https://lh3.googleusercontent.com/-pmA4NWWagTE/U7EzsPGsw1I/AAAAAAAAGiA/-p0hXIxxnbI/w640-h480-no/20140630_165125.jpg[/IMG]

And there are options on the save and exit screen to override the boot options:
[IMG]https://lh4.googleusercontent.com/-VcX2CCurVbc/U7EztYs6pRI/AAAAAAAAGiM/R-eLCCe64Ew/w640-h480-no/20140630_165134.jpg[/IMG]

If I choose the first option on the Grub screen, when a Ubuntu CD is in the drive, I can boot into my install of Ubuntu

If the CD is not in the drive when I turn on the computer I get an "efidisk read error" message.
If I then insert the CD, Ubuntu, the installed version, boots without issue.

Thanks again,
John

---

### Post by behanj on 2014-06-30
The issue I am having seems to be related to this - [http://askubuntu.com/questions/371104/efidisk-read-error]("http://askubuntu.com/questions/371104/efidisk-read-error")

The link to rEFInd is dead on there though

---

### Post by oldfred on 2014-06-30
Your settings look correct, but that you have to have DVD in drive to boot internal drive is very strange.

Are there any other UEFI settings relating to CD/DVD drive?

---

### Post by behanj on 2014-07-01
Hi,

Just an update.

I followed the directions in the link above and created the rEFInd boot cd. It worked, so I installed the Ubuntu version of it and now everything works fine.

Here's a link to the page with the Ubuntu repository and install instructions - [http://www.rodsbooks.com/refind/getting.html#ppa]("http://www.rodsbooks.com/refind/getting.html#ppa")

Thanks for all the help.

---

### Post by behanj on 2014-07-01
Hi,

Just a quick update,

I followed the instructions in the link above and installed rEFInd.

It now works without a CD in the drive

Thanks for all the help

---

