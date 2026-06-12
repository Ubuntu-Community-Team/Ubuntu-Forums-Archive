---
title: "Ubuntu won't boot after update."
date: 2021-08-11
forum: General Help
---

### Post by subfer1 on 2021-08-11
So I have urgent things to do, I booted my laptop and it said I had to do updates. I installed them and rebooted so I could get to work and then my computer wouldn't boot.

I got stuck in the HP loading screen and it would reboot on its own as it can't find a bootable system. I used an installation drive and tried boot repair, it said it worked but it did nothing. Here's the paste bin with its report:[URL="https://paste.ubuntu.com/p/Bh6MV7gtK6/"]
Ubuntu Pastebin[/URL]

I am running ubuntu 20.04.2

Any idea of what I could do?

---

### Post by aricroy on 2021-08-12
[COLOR=#242729][FONT=-apple-system]In your GNU GRUB menu screen (where you select Ubuntu, Advanced options, Memory test, Recovery, etc), you can edit the command line by pressing 'e' on the highligted line. Now, you can edit the parameters that are passed to the kernel during boot time. If you replace init with init=/bin/sh, you will escape to a root shell at an early point. From here, you can mount disks, and fix other issues.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]To see what goes on during boot you can edit the boot sequence as described above, and get rid of the 'quiet splash' section as well (or press ESC during boot when you see the splash screen or everything is black).[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]I would pay attention to the boot sequence as the text flies by, it might hang at a certain point. That's your clue. ;)[/FONT][/COLOR]

---

### Post by tea for one on 2021-08-12
```
Ubuntu, with Linux 5.11.0-25-generic   729bd14e-002c-4277-b0fc-c2bc062696f0
Ubuntu, with Linux 5.8.0-63-generic   729bd14e-002c-4277-b0fc-c2bc062696f0
```

There have been a few forum posts about boot problems with the 5.11 kernel .

Can you reach the Grub menu and select the 5.8 kernel?

---

### Post by subfer1 on 2021-08-12
I can't see the Grub menu at all. All I get is a black screen and after some seconds, my laptop reboots and it continues to do this on a loop. I hit ESC and went into the boot options. If I look for EFI boot, I can boot ubuntu from there. But then I have to repeat the steps and my laptop won't do the automatic boot as it should...

Could you guys redirect me to a thread in which I can find how to select the kernel? I don't really know if that will help, but I'm willing to try...

Thanks!

---

### Post by tea for one on 2021-08-13
> **subfer1 said:**
> If I look for EFI boot, I can boot ubuntu from there. But then I have to repeat the steps and my laptop won't do the automatic boot as it should.

As you can boot Ubuntu via EFI, does it work OK?

If it is working normally, can you post the output from:-
```
uname -r
```

---

### Post by subfer1 on 2021-08-29
> **tea for one said:**
> As you can boot Ubuntu via EFI, does it work OK?

If it is working normally, can you post the output from:-
```
uname -r
```

Hi, sorry that it took me so long, but my work has been insane... I ran that in terminal and got this:
5.11.0-27-generic

I have realized I can boot through hitting "Esc" to find my bios options and then I can go into EFI boot, but that is a pain to do every time I turn on my laptop... I have googled and dug into forums for a way to change my grub version, but have had no luck. I might be doing it wrong and also might not even be doing the right thing...

Any advice you have will be welcome. 

Thanks!

---

### Post by oldfred on 2021-08-29
Your Windows boot entry is using wrong GUID/partUUID??

```
Boot0003* Windows Boot Manager    HD(2,GPT,[COLOR=#ff0000]b27c2518-5110-4781-a7de-baa94737f255[/COLOR],0xe1800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0004* ubuntu    HD(1,GPT,[COLOR=#ff0000]de1b99a8-722b-40da-aaa4-b4b0e2275ef1[/COLOR],0x800,0x100000)/File(EFIubuntushimx64.efi)
sda                                                                                                   
&#9500;&#9472;sda1 vfat     C161-D078                            [COLOR=#ff0000]de1b99a8-722b-40da-aaa4-b4b0e2275ef[/COLOR]1             EFI System Partition
```

You can see that directly
 sudo efibootmgr -v #should have GUID/partUUID of ESP.
 lsblk -o +PARTUUID /dev/sda

You only have one ESP, so both Windows & Ubuntu are using that ESP. 
Did you recreate the FAT32 partition when you installed Ubuntu?
You do not show Windows boot files at all in ESP.
You would need a Windows repair/recovery flash drive booted in UEFI mode,and run a full set of Windows repairs. 
Boot-Repair cannot fix most Windows issues.

---

### Post by subfer1 on 2021-09-02
> **oldfred said:**
> Your Windows boot entry is using wrong GUID/partUUID??

```
Boot0003* Windows Boot Manager    HD(2,GPT,[COLOR=#ff0000]b27c2518-5110-4781-a7de-baa94737f255[/COLOR],0xe1800,0x32000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...a................
Boot0004* ubuntu    HD(1,GPT,[COLOR=#ff0000]de1b99a8-722b-40da-aaa4-b4b0e2275ef1[/COLOR],0x800,0x100000)/File(EFIubuntushimx64.efi)
sda                                                                                                   
&#9500;&#9472;sda1 vfat     C161-D078                            [COLOR=#ff0000]de1b99a8-722b-40da-aaa4-b4b0e2275ef[/COLOR]1             EFI System Partition
```

You can see that directly
 sudo efibootmgr -v #should have GUID/partUUID of ESP.
 lsblk -o +PARTUUID /dev/sda

You only have one ESP, so both Windows & Ubuntu are using that ESP. 
Did you recreate the FAT32 partition when you installed Ubuntu?
You do not show Windows boot files at all in ESP.
You would need a Windows repair/recovery flash drive booted in UEFI mode,and run a full set of Windows repairs. 
Boot-Repair cannot fix most Windows issues.

Oh wow, no I don't have windows on this laptop, just ubuntu. This error happened just after I ran some updates and then next time I logged on the problem started.

So in that case I could use a windows boot usb? Even though I have no windows? I didn't create a partition for this installation either, I had just run the Ubuntu installer and done the standard installation...

Thanks for your help, I really appreciate it.

---

### Post by oldfred on 2021-09-02
UEFI keeps old boot entries until you houseclean them.
So Windows must have had a different ESP.

To delete an old UEFI boot entry.
sudo efibootmgr -v
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B

See also:
man efibootmgr

---

