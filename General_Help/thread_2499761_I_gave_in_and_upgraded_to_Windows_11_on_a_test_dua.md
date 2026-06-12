---
title: "I gave in and upgraded to Windows 11 on a test dual booted laptop"
date: 2024-08-09
forum: General Help
---

### Post by makem2 on 2024-08-09
Hi, I had a couple of identical laptops, one just running Windows 10 for the missus and one dual booting Xubuntu.

I decided to give Windows 11 a try and started with the single OS one. No problems, went easy.

So, I crossed my arms, fingers, legs and toes (Couldn't manage the ears though lol) and went for it on the dual boot. Amazing, no problems, went easy AND Grub survived! First time ever for me. [IMG]https://ubuntuforums.org/images/icons/icon11.png[/IMG]

I had read somewhere that MS had been paying the fines from it's bulging coffers for years but had eventually been forced to stop it's evil ways and leave the boot-loader intact instead of commandeering it.

If I had not read that I may have postponed MY upgrade indefinitely.

I have a desktop, also dual booted with Windows and Xubuntu. Shall I risk it? To be, or not to be, that is the question?

Before I decide, I ask advice from those who went before, (I know I should not be a follower but take the bit and get on with it.) but I am chicken [IMG]https://ubuntuforums.org/images/icons/icon8.png[/IMG]

Please, would any non-chickens relate their experience, that I may tread in their footsteps?

---

### Post by yancek on 2024-08-09
>  I had read somewhere that MS had been paying the fines from it's bulging  coffers for years but had eventually been forced to stop it's evil ways  and leave the boot-loader intact instead of commandeering it.

Not sure what you are referring to here but microsoft has been paying 'fines' and has been sued and lost numerous time for stealing from others but I don't know about changing their 'evil ways'.  UEFI systems are different if that is what you might mean as they don't overwrite code in the MBR but simply put boot code for the OS on a separate partition and the user simply needs to go into the BIOS firmware to set the OS s/he want to first boot priority.

If windows 11 was preinstalled it is almost certain to be a UEFI install so you would simply boot and install Xubuntu in UEFI mode, particularly if both systems are on the same physical hard drive.  Use your notes from your other install to do the new install and maybe read through some online tutorials on dual booting with windows UEFI.

---

### Post by makem2 on 2024-08-10
> **yancek said:**
> Not sure what you are referring to here but microsoft has been paying 'fines' and has been sued and lost numerous time for stealing from others but I don't know about changing their 'evil ways'.  UEFI systems are different if that is what you might mean as they don't overwrite code in the MBR but simply put boot code for the OS on a separate partition and the user simply needs to go into the BIOS firmware to set the OS s/he want to first boot priority.

If windows 11 was preinstalled it is almost certain to be a UEFI install so you would simply boot and install Xubuntu in UEFI mode, particularly if both systems are on the same physical hard drive.  Use your notes from your other install to do the new install and maybe read through some online tutorials on dual booting with windows UEFI.

Wow, sorry my post must have mislead you.

1. Windows 10 and/or 11 was not preinstalled
2. I installed Xubuntu years ago after first installing windows 10 on a bare metal machine.
3. The system is UEFI and has windows 10 on it along with Xubuntu.
4. I want to upgrade windows 10 to windows 11 using the windows 10 upgrade method
.

This is exactly, step by step what I did on the laptop which was also dual booted and it went smoothly. My concern now is that it may not on my desktop main machine.

MS 'evil ways' meant they mess with the bootloader and it was necessary to sort out grub after upgrading windows.

Have you upgraded windows 10 to 11 on a dual boot desktop machine, ie. not a chicken?

---

### Post by yancek on 2024-08-10
If  you have windows installed, the first thing to do would be to use Disk Management ln window to shrink the largest windows partition to create free/unallocated space for your install of Xubuntu on the computer.  There is no point in trying to create  a partition for Xubuntu from windows as you will have to do that with Xubuntu and create a Linux filesystem for Xubuntu and you cannot do that in windows.  After doing this, you should reboot to windows to see if you have any problems and it is usually suggested that you also run chkdsk in windows after rebooting.

When you install Xubuntu, you need to access the BIOS and make sure Xubuntu is set to boot first.  You should have options in the BIOS to boot either windows or Xubuntu.  Setting Xubuntu to boot first should give you a Grub menu to boot either system.  I don't believe windows will boot a Linux system from bcd on an EFI install without 3rd party software.

Additionally, some window updates will set windows to first boot in the BIOS so you will need to go into the BIOS and change back to Xubuntu to first boot.  On windows updates, you will not be asked nor will you be informed that this will happen but it should be a simple process to make the change in the BIOS.

I don't have windows 11 and don't intend to use it but the potential problems are what I describe above.

---

### Post by makem2 on 2024-08-10
> **yancek said:**
> If  you have windows installed, the first thing to do would be to use Disk Management ln window to shrink the largest windows partition to create free/unallocated space for your install of Xubuntu on the computer.  There is no point in trying to create  a partition for Xubuntu from windows as you will have to do that with Xubuntu and create a Linux filesystem for Xubuntu and you cannot do that in windows.  After doing this, you should reboot to windows to see if you have any problems and it is usually suggested that you also run chkdsk in windows after rebooting.

When you install Xubuntu, you need to access the BIOS and make sure Xubuntu is set to boot first.  You should have options in the BIOS to boot either windows or Xubuntu.  Setting Xubuntu to boot first should give you a Grub menu to boot either system.  I don't believe windows will boot a Linux system from bcd on an EFI install without 3rd party software.

Additionally, some window updates will set windows to first boot in the BIOS so you will need to go into the BIOS and change back to Xubuntu to first boot.  On windows updates, you will not be asked nor will you be informed that this will happen but it should be a simple process to make the change in the BIOS.

I don't have windows 11 and don't intend to use it but the potential problems are what I describe above.

Please, Windows 10 and Xubuntu are already installed and have been so for years as I said in my first post?

---

### Post by dragonfly41 on 2024-08-10
I will give it a shot.
My policy is that Windows is necessary to be compatible with other parties who are locked in the Microsoft deadly embrace. My old Dell Inspiron is incompatible with the Windows 11 configuration requirement. I will be buying a desktop (Optiplex, not laptop) which is compatible w ith Windows 11.

Regarding “sharing" a drive between Windows and Ubuntu (shrinking the drive partition as suggested) my policy is to leave well alone and put as much distance as I can between Windows and Ubuntu. Therefore I opt for external docking bay holding Ubuntu which operates quite nicely through USB 3.0 port. It is easier to swap out drives in caddies. I have multiple caddies/SSD's.
On the matter of dual booting although standard grub models work well I opt for the third party rEFInd installation. This runs alongside the usual grub.
I see that you have a laptop. Another policy I apply is to purchase separate desktop tower PC and display, although there might be portability requirements for you dictating use of laptop. You can add a portable SSD to your laptop. Carry caddy separately as a precaution against theft or loss of your travelling host laptop.
[https://uk.crucial.com/ssd/x9/ct1000x9ssd9](https://uk.crucial.com/ssd/x9/ct1000x9ssd9)
Install Ubuntu on portable caddy using separate LiveUSB.
In fact you can install an NTFS partition in the portable caddy to hold Windows files either:
Windows only access
shared between Windows and Ubuntu.


In Windows you can try (trial) EasyUEFI.
[https://www.easyuefi.com/index-us.html](https://www.easyuefi.com/index-us.html)
A Swiss army knife model.


Remember the recent global outage (Windows update fiasco). Be able to boot without Windows so the rEFInd boot can be installed in the first boot partition in your external drive with Ubuntu installed. Away from Windows.

---

### Post by yancek on 2024-08-10
I read your posts again and see I misread them.  Since I don't use windows 11, have never used it and don't plan to I can't help.  I would expect that if you are successful with the upgrade to 11, there really should not be any problem other than windows setting itself to first in the BIOS boot priority but that's standard and easily repaired. Maybe someone who has actually done it will see your thread  if you are patient.   Good luck.

---

### Post by makem2 on 2024-08-10
> **yancek said:**
> I read your posts again and see I misread them.  Since I don't use windows 11, have never used it and don't plan to I can't help.  I would expect that if you are successful with the upgrade to 11, there really should not be any problem other than windows setting itself to first in the BIOS boot priority but that's standard and easily repaired. Maybe someone who has actually done it will see your thread  if you are patient.   Good luck.

Yes, I was hoping for replies from those who have done what I desire to do only. But never mind, thank you for your time.

---

### Post by makem2 on 2024-08-10
> **dragonfly41 said:**
> I will give it a shot.
My policy is that Windows is necessary to be compatible with other parties who are locked in the Microsoft deadly embrace. My old Dell Inspiron is incompatible with the Windows 11 configuration requirement. I will be buying a desktop (Optiplex, not laptop) which is compatible w ith Windows 11.

Regarding “sharing" a drive between Windows and Ubuntu (shrinking the drive partition as suggested) my policy is to leave well alone and put as much distance as I can between Windows and Ubuntu. Therefore I opt for external docking bay holding Ubuntu which operates quite nicely through USB 3.0 port. It is easier to swap out drives in caddies. I have multiple caddies/SSD's.
On the matter of dual booting although standard grub models work well I opt for the third party rEFInd installation. This runs alongside the usual grub.
I see that you have a laptop. Another policy I apply is to purchase separate desktop tower PC and display, although there might be portability requirements for you dictating use of laptop. You can add a portable SSD to your laptop. Carry caddy separately as a precaution against theft or loss of your travelling host laptop.
[https://uk.crucial.com/ssd/x9/ct1000x9ssd9](https://uk.crucial.com/ssd/x9/ct1000x9ssd9)
Install Ubuntu on portable caddy using separate LiveUSB.
In fact you can install an NTFS partition in the portable caddy to hold Windows files either:
Windows only access
shared between Windows and Ubuntu.


In Windows you can try (trial) EasyUEFI.
[https://www.easyuefi.com/index-us.html](https://www.easyuefi.com/index-us.html)
A Swiss army knife model.


Remember the recent global outage (Windows update fiasco). Be able to boot without Windows so the rEFInd boot can be installed in the first boot partition in your external drive with Ubuntu installed. Away from Windows.

I already have a dual booted windows w0 and ubuntu.

---

### Post by dragonfly41 on 2024-08-11
Returning to post #1
[COLOR=#000000]> Shall I risk it? 
It is for each of us to assess risk

I was trying to explain how to *mitigate* risk by putting distance between Ubuntu and Windows 10/11. Presomably if you were upgrading from Windows 10 to Windows 11 you would take the precaution of backing up your existing setup. A climbing rope (writing as a one time rock climber in my youth). Risks are everywhere in life.[/COLOR]

---

### Post by yancek on 2024-08-11
The only problem I would expect to have is the one I described in post 7 and that can happen after the upgrade on certain updates done from windows but is easy to resolve.  I don't know what else would be a problem as the windows update should not have any effect on your Linux partitions.  It appears there are not many windows users who have done this at these forums which is surprising.  Anyhow, good luck if you do it.

---

### Post by makem2 on 2024-08-11
> **dragonfly41 said:**
> Returning to post #1
[COLOR=#000000]
It is for each of us to assess risk

I was trying to explain how to *mitigate* risk by putting distance between Ubuntu and Windows 10/11. Presomably if you were upgrading from Windows 10 to Windows 11 you would take the precaution of backing up your existing setup. A climbing rope (writing as a one time rock climber in my youth). Risks are everywhere in life.[/COLOR]

Thank you, however I am still waiting to see if anyone has actually carried out my proposed adventure and whether they avoided the previous hassle caused by MS as I mentioned I did in post #1

I have carried out my risk assessment.

---

### Post by #&amp;thj^% on 2024-08-11
I just did it yesterday, and all went well, but I DO NOT rely on grub as my only boot manager rEFInd has proven to be invaluable for myself.

BTW this is no promise it will work on your end, with or without rEFInd.

Now I have to git rid of windows, I just don't do dual booting anymore.
```
]$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL       MOUNTPOIN
nvme0n1     disk        476.9G                            
&#9500;&#9472;nvme0n1p1 part vfat     260M  217.1M    15% SYSTEM      /boot/efi
&#9500;&#9472;nvme0n1p2 part           16M                            
&#9500;&#9472;nvme0n1p3 part ntfs   425.1G                Windows-SSD 
&#9500;&#9472;nvme0n1p4 part ntfs       2G                WinRE_DRV   
&#9492;&#9472;nvme0n1p5 part ext4    49.6G     26G    41%             /

```

---

### Post by dragonfly41 on 2024-08-11
[COLOR=#000000]> I just did it yesterday, and all went well, but I DO NOT rely on grub as my only boot manager rEFInd has proven to be invaluable for myself.[/COLOR]

[COLOR=#000000]BTW this is no promise it will work on your end, with or without rEFInd.[/COLOR]

[COLOR=#000000]Now I have to git rid of windows, I just don't do dual booting anymore.

[SIZE=5]+1 rEFInd

[SIZE=2]You can also open a Microsoft 365 account in Ubuntu.[/SIZE][/SIZE][/COLOR]

---

### Post by makem2 on 2024-08-11
> **1fallen said:**
> I just did it yesterday, and all went well, but I DO NOT rely on grub as my only boot manager rEFInd has proven to be invaluable for myself.

BTW this is no promise it will work on your end, with or without rEFInd.

Now I have to git rid of windows, I just don't do dual booting anymore.
```
]$ lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME        TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL       MOUNTPOIN
nvme0n1     disk        476.9G                            
&#9500;&#9472;nvme0n1p1 part vfat     260M  217.1M    15% SYSTEM      /boot/efi
&#9500;&#9472;nvme0n1p2 part           16M                            
&#9500;&#9472;nvme0n1p3 part ntfs   425.1G                Windows-SSD 
&#9500;&#9472;nvme0n1p4 part ntfs       2G                WinRE_DRV   
&#9492;&#9472;nvme0n1p5 part ext4    49.6G     26G    41%             /

```

I only keep windows because I play an occasional game not available on Ubuntu and Chinese banks favour it.

So you find rEFInd more 'safe' than grub? I must look into the advantages then because I had never heard of it.

---

