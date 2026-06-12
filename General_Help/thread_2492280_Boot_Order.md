---
title: "Boot Order"
date: 2023-11-06
forum: General Help
---

### Post by BNZBKK on 2023-11-06
I recently bought a used Acer Veriton with Windows 10 installed in an SSD 124Gb HD. 
I 'clean' installed Unbuntu 22.04 into a new internal 1TB HD but it won't boot cleanly ie; it goes to a line of script (if I'm lucky) then I have to F2 it to boot. If anyone could tell me the correct boot order or how to fix this so that it boots up normally I would be very grateful.

---

### Post by VMC on 2023-11-06
The Hard Disk Drive Priority has other options. What are they?

---

### Post by oldfred on 2023-11-06
Do you have the latest UEFI from Acer?
Many Acer need Control-S in UEFI to open more settings.
Most Acer also seem to need "trust" setting in UEFI on ubuntu entry. 

If you have to set UEFI password to get more settings, be sure not to lose that or reset to blank or you may later find you cannot fix anything.

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

---

### Post by Yellow Pasque on 2023-11-06
Not sure if it's related, but you'll want to disable the chassis intrusion detection unless you're really worried about people physically tampering with your computer. Even if you're worried about it, you probably want to disable it for a few boots to reset the message and then re-enable it.
[https://community.acer.com/en/kb/articles/136-acer-veriton-desktop-chassis-intrusion-message](https://community.acer.com/en/kb/articles/136-acer-veriton-desktop-chassis-intrusion-message)

---

### Post by BNZBKK on 2023-11-07
> **VMC said:**
> The Hard Disk Drive Priority has other options. What are they?


Thanks for your attention,

1. Photo of the HDD Priority

2. No Root. Undecipherable to me !

3. Partition, here's where it all started to go wrong.



I tried to disconnect the first small 124Gb HD and connect the cables to the new 1 TB drive to see if that would fire it up but nothing.
The first small drive doesn't matter to me.
I reconnected back to the original order and installed 22,04 but a PITA to get to for the wife ..heh.

---

### Post by BNZBKK on 2023-11-07
[SIZE=4]**oldfred**
[/SIZE]
I'm reading your links and getting an education ...heh. Thank you for your response,

---

### Post by BNZBKK on 2023-11-07
> **Yellow Pasque said:**
> Not sure if it's related, but you'll want to disable the chassis intrusion detection unless you're really worried about people physically tampering with your computer. Even if you're worried about it, you probably want to disable it for a few boots to reset the message and then re-enable it.
[https://community.acer.com/en/kb/articles/136-acer-veriton-desktop-chassis-intrusion-message](https://community.acer.com/en/kb/articles/136-acer-veriton-desktop-chassis-intrusion-message)


Thanks, I'll give it a try.

---

### Post by dragonfly41 on 2023-11-07
Installing efibootmgr and running efibootmgr in terminal will give more info.

---

### Post by yancek on 2023-11-07
Posting the output from:  sudo efibootmgr run in a terminal from Ubuntu would be a good start as suggested above.

The image of Installation Type you posted seems to be the 1TB drive but there is no Linux partition with a Linux filesystem shown.  The 2 largest partitions are FAT32 and ntfs and you won't get a working Linux on either filesystem.  In addition, that image  does not show an EFI partition.  Do you have an EFI partition on the other drive?  Windows 10 presinstalled would certainly be EFI.  Do you have data on sda2 and sda3, the 2 windows partitions?  If you want Ubuntu on that drive you need to create a partition with a Linux filesystem format and formatting that partition will overwrite any data.  As to the no root mount point defined, during the install, there will be an option to select a mount point and you need to select the / option which signifies the root of the filesystem.

The first step would be to determine if both or either install is EFI and if the EFI partition is used from the first drive.

---

### Post by oldfred on 2023-11-07
If system supports two drives, the small SSD would be great for / (root) and then you can have /home and/or data on HDD.
It would be large enough for /home, if you moved all your user data to HDD, but that is a bit more advanced as you have to manually create another partition, set ownership & permissions and edit fstab with new entry. With /home all that is done during install, if you select it.

If you boot in UEFI mode, which you should, you need both an ESP - efi sytem partition which is FAT32 with esp,boot flags and / (root) partition. If created in advance, you have to choose (change) to use partition as /.

---

### Post by BNZBKK on 2023-11-08
> **yancek said:**
> Posting the output from:  sudo efibootmgr run in a terminal from Ubuntu would be a good start as suggested above.

The image of Installation Type you posted seems to be the 1TB drive but there is no Linux partition with a Linux filesystem shown.  The 2 largest partitions are FAT32 and ntfs and you won't get a working Linux on either filesystem.  In addition, that image  does not show an EFI partition.  Do you have an EFI partition on the other drive?  Windows 10 presinstalled would certainly be EFI.  Do you have data on sda2 and sda3, the 2 windows partitions?  If you want Ubuntu on that drive you need to create a partition with a Linux filesystem format and formatting that partition will overwrite any data.  As to the no root mount point defined, during the install, there will be an option to select a mount point and you need to select the / option which signifies the root of the filesystem.

The first step would be to determine if both or either install is EFI and if the EFI partition is used from the first drive.


Ok thanks and I understand most of what you're saying, so let's start with the Terminal pic ...not much there

---

### Post by oldfred on 2023-11-08
Please do not post terminal output as screen shots. Just post inside code tags.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

I prefer 
sudo efibootmgr -v

```
[FONT=monospace][COLOR=#54ff54]**fred@Z170-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo efibootmgr -v [/COLOR]
[sudo] password for fred:  
BootCurrent: 0001 
Timeout: 1 seconds 
BootOrder: 0001,0003,0002,0005,0006
Boot0001* jammy HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\JAMMY\SHIMX64.EFI) 
Boot0002* lunar HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\LUNAR\SHIMX64.EFI) 
Boot0003* mantic        HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\MANTIC\SHIMX64
.EFI) 
Boot0005* Fedora        HD(1,GPT,e58602b1-8fc4-46d1-991f-1d6511d9cdf4,0x800,0xff1b9)/File(\EFI\FEDORA\SHIM.EF
I)..BO 
Boot0006* ubuntu        HD(1,GPT,c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX6
4.EFI)..BO 



[/FONT]
```

---

### Post by BNZBKK on 2023-11-09
> **oldfred said:**
>  

I prefer 
sudo efibootmgr -v

 

I did try that as well but the result was the same as posted.

---

### Post by Rubi1200 on 2023-11-09
Your screenshot shows the install of efibootmgr but I do not see the output of oldfred's command:
```
sudo efibootmgr -v
```

Please run this command and copy the results from the terminal.

Then reply with Go Advanced and paste into the reply and then wrap with # tags.

Thanks.

---

