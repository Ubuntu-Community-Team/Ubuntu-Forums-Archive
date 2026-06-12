---
title: "Can't install UbuntuStudio alongside Windows 8"
date: 2014-07-04
forum: General Help
---

### Post by Ardeshir on 2014-07-04
HI .
I have a 500 GB H.D.D and I dedicated it all to Ubuntu before .
But later I needed Windows 8 , I couldn't install it and created a thread in which I was told I can't install Windows 8 After Ubuntu :
[http://ubuntuforums.org/showthread.php?t=2232624](http://ubuntuforums.org/showthread.php?t=2232624)

Now I need some music and video creation softwares both in Windows and Linux and I'm trying to install UbuntuStudio after Windows 8 , but whatever I do I can't see the option "Install UbuntuStudio alongside Windows" .
And when I choose "Something else" or open GParted , I see the whole 500 GB is marked as unallocated (in live mode) , BUT I can see my 250 GB Windows Volume there . (I kept the other 250 GB for UbutnuStudio)
Also when I open GParted this notification appears :
> /dev/sda contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?

[COLOR=#000000](Yes/No)[/COLOR]
It doesn't matter whether I choose Yes or No , It still shows the whole H.D.D as unallocated .

My Windows 8 hasn't UEFI firmware , but my motherboard supports it . I tried both UEFI and legacy mode , I still couldn't see the "Install alongside ..." option .

Also , I did try everything google search results in ubuntuforums and askubuntu and official documentations (including UEFI and SecureBoot) believe me , none of them worked .
Don't give me link to other solutions , I tried all of them and am trying this installation for 2 days and have booted UbuntuStudio live for more than 20 times with different settings . Also installed Windows 8 three times with 3 different hard allocation .

+ I have nothing important in my H.D.D , if I need to format the whole H.D.D let me know , that's possible .
If any furhter information is needed tell me .

Thanks .

---

### Post by Ardeshir on 2014-07-09
HI Everyone . I still need the answer .
Or at least if you know anyone who can help me. THANKS!

---

### Post by Elfy on 2014-07-10
*Thread moved to **General Help**.*

---

### Post by oldfred on 2014-07-10
Your issue is more how you are booting install media.
Both Windows and Ubuntu will only install in the same mode as you boot install media. And both should give you two choices UEFI or BIOS if system is UEFI capable.

Always best to have both systems in either UEFI or both BIOS.
Windows only boots from gpt partitioned drives with UEFI, so when you booted Windows installer in BIOS mode it would not install. If you had booted in UEFI mode it should have installed, but with UEFI Windows does need an extra partition or two.

And when you force Windows to install in BIOS mode over a gpt partitioned drive it converts drive to MBR(msdos) but leaves the backup gpt partition table. Or it does not fully convert it. Then Linux installer sees both MBR and gpt partitions and does not know what to do.

If you want Ubuntu in BIOS mode just remove backup gpt partition table. Or reinstall Windows in UEFI mode. 
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Even if in BIOS mode you still need fast boot off in Windows. In BIOS mode there is no secure boot.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
Windows 8 info
[http://technet.microsoft.com/en-us/library/hh824947.aspx](http://technet.microsoft.com/en-us/library/hh824947.aspx)

---

