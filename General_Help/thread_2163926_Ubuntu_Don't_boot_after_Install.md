---
title: "Ubuntu Don't boot after Install"
date: 2013-07-20
forum: General Help
---

### Post by AlbionManch on 2013-07-20
Last day i bought a pc which was using windows7 default. Then i connected my liveI USB (12.04) to my computer and installed with deleting windows. Then I reboot my computer and unconnected my Live USB. but bios didn't boot ubuntu so i tried several times.othin happened! I reinstalled ubuntu 2 or 3 times but bios was still not booting ubuntu. I thougt it was a bug of12.04 so i made a 13.10 live usb but this didn't work either. I installed Windows XP from my old windows CD. And i installed ubuntu via wubi but it gave me that error:
```
try (hd0,0) NTFS5
```
so i decited to try installing from live usb one more time but it didn't worked again. So i made a boot-repair-disk USB  and tried it. It didn't worked but it said it has reinstalled grub succesfully. Then i tried to erase all the paririons from gparted and i did.  but when i install ubuntu again, the same problem! Didn't boot! Please help me i am at a loss!

Sorry for my english... :D

---

### Post by Boab1993 on 2013-07-20
Hi There AlbionManch,

Its a fairly common problem with WUBI
Sounds like you have a file called 'root.disk' missing in a directory called \ubuntu\disks\
[COLOR=#000000]
Have a look here [/COLOR][http://ubuntu-with-wubi.blogspot.co.uk/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.uk/2011/08/missing-rootdisk.html)[COLOR=#000000]
[/COLOR]

---

### Post by Mark Phelps on 2013-07-20
Wubi has been discontinued as of Ubuntu 13.04.  

IF you want to use Wubi, which is not intended for long-term use, you will have to use Ubuntu 12.10 or earlier.

---

### Post by AlbionManch on 2013-07-20
> **Boab1993 said:**
> Hi There AlbionManch,

Its a fairly common problem with WUBI
Sounds like you have a file called 'root.disk' missing in a directory called \ubuntu\disks\
[COLOR=#000000]
Have a look here [/COLOR][http://ubuntu-with-wubi.blogspot.co.uk/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.co.uk/2011/08/missing-rootdisk.html)[COLOR=#000000]
[/COLOR]
Okey i can make it via wubi thank :)!I will try it.

1. But after wubi install can i delete windows and run ubuntu only? I think no.
2. But what if i want to install ubuntu 13.10 via live USB? How can i install with it? Why ubuntu live USBs and CDs don't make ubuntu boot after install? 

Because i want only ubuntu not windows. Thank for both replies.

---

### Post by Boab1993 on 2013-07-20
Im afraid no you can't run ubuntu solely of wubi, sadly
To make a live usb you have to first download a '.iso' file of the ubuntu you want - for the standard ubuntu download it of the main site here:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Make sure you know where it has downloaded to.

To put the disk image(.iso) onto a usb download the universal usb creator:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
(The download link is at the bottom of the page)

Once you've done that, follow these instructions:

[http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Hope this helps and good luck!

Post your results here

---

### Post by AlbionManch on 2013-07-20
I have downloaded Ubuntu 12.04.02 Alternate Iso and I tried to install but It gave me this Error:

```
Installation Step Failed:
An installation step failed. You can try to run failing item again from the menu or skip it and choose someting else.The failing step is :Select and Install Sofware
```

So... What can i do? Any suggestions?

Edit:Then I tried to install from 13.10 Live USB alongside corrupted one and It is not booting still. Is it a bios bug or a bios setting?

---

### Post by oldfred on 2013-07-20
Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by AlbionManch on 2013-07-20
I have NVDIA G105M with Intel Core 2 Duo Ins&#305;de. Which Is Now formatted whit a broken installation of 12.04.02 and a 13.10 (Saucy Salamender) ubuntu install. But nothing boot up when I open it.
So heres is the info after repair (which is not worked):
[http://paste.ubuntu.com/5895001/](http://paste.ubuntu.com/5895001/)
And Here is the Boot Info from boot info section:
[http://paste.ubuntu.com/5895006/](http://paste.ubuntu.com/5895006/)
Thanks for interest :D

---

### Post by Boab1993 on 2013-07-20
Hmm, i would try installing 12.04 using the desktop CD and the universal usb installer, see how that goes.

Make sure you format your usb stick to correct format!

Report back, if it doesn't work we'll think of something!

---

### Post by oldfred on 2013-07-20
The grub in the MBR is booting from sda1 or 12.04.

But is it really booting and you are getting a black screen? Since you have two installs you should get grub menu, if not hold shift key from BIOS until you get menu.

Any version of nVidia needs nomodeset. You can add that with e on grub menu and edit linux line to replace spash quiet with nomodeset. Recovery mode also has nomodeset as default parameter.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Sometimes BIOS settings changes or other boot parameters may be required.

---

### Post by AlbionManch on 2013-07-20
When i hold down shift Computer says:
```
GRUB Loading.
```
But nothing happens. I will try to install ubuntu in nomodeset and share you the result. Thanks for advice.

---

