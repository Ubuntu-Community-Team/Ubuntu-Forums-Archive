---
title: "Grub only displays 'GRUB' when using ntloader"
date: 2007-05-03
forum: General Help
---

### Post by Eoin on 2007-05-03
Hi, I know the title sounds a bit cryptic, but that's because there is no other information being displayed. I installed Ubuntu (7.04) and selected to install Grub just to the hard disk and not MBR. Everything seemed to work and while if I selected the disk Ubuntu was installed to through the BIOS then I could boot. Well it wasn't all rosy, you'd need to edit the Grub menu command from (hd1) to (hd0) but that was minor.

Next thing I followed the standard instructions to 'sudo dd ...' and copy that binary file to the Windows disk and edit 'boot.ini' appropriately. Having done that I could boot Ubuntu from the ntldr.

However then I wipe my XP install and changed to Server 2003. Now whenever I select the Ubuntu choice I just get a blank screen with the word 'GRUB' displayed in the top left. The computer doesn't seem to respond any keypresses beyond a Ctrl-Alt-Del.

If I use the BIOS to select the Linux disk then I can boot as before so it doesn't seem like anything's been changed. 

A Google turned up this [post](http://www.mail-archive.com/bug-grub@gnu.org/msg10914.html) which didn't throw up any real solution. I tried bootpart as the 'poster' mentioned but could quite seem to get it to work. If it helps here is My partition layout.

```
C:\>bootpart
Boot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : http://www.winimage.com and http://www.winimage.com/bootpart.htm
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0 : f8000b1
 0 : C:* type=7  (HPFS/NTFS), size= 117210208 KB, Lba Pos=63
Physical number of disk 1 : f8000b2
 1 : D:* type=83  (Linux native), size= 28748286 KB, Lba Pos=63
 2 : D:  type=5  (Extended), size= 1277167 KB, Lba Pos=57496635
 3 : D:  type=82   (Linux swap), size= 1277136 KB, Lba Pos=57496698
Physical number of disk 2 : d31bd31b
 4 : E:  type=7  (HPFS/NTFS), size= 72597703 KB, Lba Pos=63
Physical number of disk 3 : 9d9ca89f
 5 : F:* type=7  (HPFS/NTFS), size= 120045681 KB, Lba Pos=63
```

C: is Vista, D: is Ubuntu and E: Server 2003.

---

### Post by Herman on 2007-05-03
Try GAG Boot Manager instead, links,
[GAG Boot Manager]("http://gag.sourceforge.net/") - The home page for GAG Boot Manager, and [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm") - web page made by me about how to use GAG with Ubuntu. (Presuming you have some objection to Grub).

It is a much better idea to dual boot with open source boot loaders/managers as they rock and the commercial ones suck.  :)

Regards, Herman :)

---

### Post by Eoin on 2007-05-07
Hi Herman, thanks for the suggestion. I'd really like to stick with the NT Loader approach because it is set up and working. Getting other bootloaders to work with Vista seems like it'd be a big pain.

To update my earlier post, I decided Server 2003 was impractical to use a a general purpose so went back to XP Pro. Grub still displayed the problem. So I tried completely wiping the Ubuntu disk and reinstalling, again though no luck.

I'm thinking that switching from Grub to LILO to boot Ubuntu might be a wise next step as I've had success before getting the NT Loader to boot LILO. However that time everything seemed to stop working after a routine update install a new kernel (this was back a few weeks using betas of 7.04). 

Would anyone have advice, or a link perhaps, on using Ubuntu with LILO?

Thanks all, and thanks Herman for your reply.

---

### Post by Computer Guru on 2007-05-07
You need to use the "lba" tag with bootpart to get it to work.

---

### Post by Eoin on 2007-05-07
Hi Computer Guru, thanks I tried that but no joy, I keep getting the following response with or without lba

> BootPart 2.60 Bootsector (c) 1993-2005 Gilles Vollant 
[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm).
Loading new partition.
Bootsector from C.H. Hochsttter.
Cannot load from harddisk.
Insert Systemdisk and press any key....

---

### Post by Herman on 2007-05-07
Eoin,
You're in good hands with Computer Guru helping you.
>  and selected to install Grub just to the hard disk and not MBR You mean to the first sector of the Ubuntu partition probably.
> Next thing I followed the standard instructions to 'sudo dd ...' and copy that binary file to the Windows disk and edit 'boot.ini' appropriately. Having done that I could boot Ubuntu from the ntldr.

However then I wipe my XP install and changed to Server 2003. Now whenever I select the Ubuntu choice I just get a blank screen with the word 'GRUB' displayed in the top left. The computer doesn't seem to respond any keypresses beyond a Ctrl-Alt-Del.
 So obviously you re-did the 'dd' command bit again and made a brand new ubuntu.bin file eh? 
> I decided Server 2003 was impractical to use a a general purpose so went back to XP Pro. Grub still displayed the problem. So I tried completely wiping the Ubuntu disk and reinstalling, again though no luck.
 Hmmm.
> I'm thinking that switching from Grub to LILO to boot Ubuntu might be a wise next step as I've had success before getting the NT Loader to boot LILO. However that time everything seemed to stop working after a routine update install a new kernel (this was back a few weeks using betas of 7.04). 
 Yes, it might be better to use Lilo, but yes, you do have to run /sbin/lilo to update Lilo when there is a kernel update. You can install Lilo in Ubuntu using Synaptic Package Manager. You don't have to delete Grub. they both get along well together and peacefully share the same /boot directory. If you want to read my notes on Lilo, here's the link, [LiLo Page]("http://users.bigpond.net.au/hermanzone/p4.html")

You will need to revert your /etc/fstab file to the old style, with the UUID filesystem ID numbers hashed out if you want to use Lilo these days. There is an illustrated step-by step how-to in that link I just gave you. 

Regards, Herman  :)

---

### Post by Eoin on 2007-05-07
> **Herman said:**
> So obviously you re-did the 'dd' command bit again and made a brand new ubuntu.bin file eh? 
I did yeah and also checked the file in a hex editor out of curiosity, it hadn't changed at all from the earlier one.

That page of yours seems to be a gold mine of information, I'll dig into it and hopefully progress further, thanks very much.

---

