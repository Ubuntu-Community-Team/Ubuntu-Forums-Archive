---
title: "How To Resize /home partition ?"
date: 2017-05-12
forum: General Help
---

### Post by heron1337 on 2017-05-12
hey  i have a problem with resizing a /home partiotin i didnt assign enough space and i need to resize it, i was trying to use gparted liveusb but didnt work for me, any other solutions pls?

[http://prntscr.com/f71p5c](http://prntscr.com/f71p5c)

/sda11 6gb

---

### Post by Dennis N on 2017-05-12
Your home partition is mounted (note the key symbol). You must unmount a partition to resize it. That said, if you are resizing sda11, you have another problem, since there is no unallocated space next to it that you would need to expand it.

---

### Post by heron1337 on 2017-05-12
> **Dennis N said:**
> Your home partition is mounted (note the key symbol). You must unmount a partition to resize it. That said, if you are resizing sda11, you have another problem, since there is no unallocated space next to it that you would need to expand it.

ye i know i was reading about it thats why i tried gparted but my bios dont see my pendrive so anyway can u explain step by step how to do this ?

---

### Post by oldfred on 2017-05-12
You have to figure out why your UEFI/BIOS does not boot flash drive.
Did you change settings like turn on UEFI Secure boot or turn off allow USB boot in UEFI settings?

It also looks like you left Windows fast start up or hibernation on. The red icon says gparted cannot see your NTFS sda5 partition. 
The error on your sda4 partition is ok. That is required by Microsoft to be unformatted as the Microsoft system reserved partition. But then gparted sees it as unformatted and notes that.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

      [/URL]
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions
[/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]
[/URL] 

    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by Dennis N on 2017-05-12
You can only expand into unallocated space. To expand to any useful extent, you would need to delete the ntfs partitions 6,7,8 giving you about 26 GiB more unallocated space, but those may be essential for your computer and windows to work properly. You have to look into what those are for, and if they can be safely removed, and if you might need them - to restore system for example.

Possibility 2:

Theoretically, you could try to shrink 10 by 8-10 GiB since you only have 5 in use, leaving unallocated space at it's immediate right as a result. Then try to expand 11 into the unallocated space you created by that. This is a most risky procedure, so be sure to back up all data.

Possibility 3 is to just reinstall:

You could delete 10 and 11, make two new partitions in that space, this time with a larger home, and reinstall. Or make just the root partition and not use a separate home.

---

### Post by heron1337 on 2017-05-12
Ye i was looking on other forums on ppl threads and i found something similar to mine and they said that maybe the secure boot is enabled or something so i restart my computer but everything was alright they also said that i should change uefi to legacy but after that windows is botting first without grub menu and i have to shut down windows then run boot menu and then open ubuntu its so ****ed up now... I will try to turn off windows fast start like you said and i take some pictures of my bios settings. BRB

---

### Post by heron1337 on 2017-05-12
> **Dennis N said:**
> You can only expand into unallocated space. To expand to any useful extent, you would need to delete the ntfs partitions 6,7,8 giving you about 26 GiB more unallocated space, but those may be essential for your computer and windows to work properly. You have to look into what those are for, and if they can be safely removed, and if you might need them - to restore system for example.

Possibility 2:

Theoretically, you could try to shrink 10 by 8-10 GiB since you only have 5 in use, leaving unallocated space at it's immediate right as a result. Then try to expand 11 into the unallocated space you created by that. This is a most risky procedure, so be sure to back up all data.

Possibility 3 is to just reinstall:

You could delete 10 and 11, make two new partitions in that space, this time with a larger home, and reinstall. Or make just the root partition and not use a separate home.

i read that if i want to delete ubuntu i need cd or iso with my win, because registry is overwrited something like that idk, is it right ?

---

### Post by heron1337 on 2017-05-12
> **oldfred said:**
> You have to figure out why your UEFI/BIOS does not boot flash drive.
Did you change settings like turn on UEFI Secure boot or turn off allow USB boot in UEFI settings?

It also looks like you left Windows fast start up or hibernation on. The red icon says gparted cannot see your NTFS sda5 partition. 
The error on your sda4 partition is ok. That is required by Microsoft to be unformatted as the Microsoft system reserved partition. But then gparted sees it as unformatted and notes that.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

      [/URL]
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions
[/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

[URL="https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions"]
[/URL] 

    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

My Bios:
[http://screenshot.sh/n9LMOcO7F4Wwm](http://screenshot.sh/n9LMOcO7F4Wwm)
[http://screenshot.sh/m3BjUz8dgFATA](http://screenshot.sh/m3BjUz8dgFATA)
[http://screenshot.sh/m7BI1XzETzJjU](http://screenshot.sh/m7BI1XzETzJjU)

---

### Post by Dennis N on 2017-05-12
> i read that if i want to delete ubuntu i need cd or iso with my win, because registry is overwrited something like that idk, is it right ? 

My knowledge of Windows after XP is minimal (have rarely used Windows since then - it's not on any of my computers) so I defer to others on this question. But the general rule is operate on Linux partitions with Linux tools (like gparted) and operate on Windows partitions with Windows tools. 10 and 11 are Linux partitions.

If I had to do it, I would back up all important data and do option 2 first (shrink partition 10 from the right, expand partition 11 to the left). It may very well work out fine, and it's done.  If not, use option 3.

---

### Post by heron1337 on 2017-05-12
> **Dennis N said:**
> My knowledge of Windows after XP is minimal (have rarely used Windows since then - it's not on any of my computers) so I defer to others on this question. But the general rule is operate on Linux partitions with Linux tools (like gparted) and operate on Windows partitions with Windows tools. 10 and 11 are Linux partitions.

If I had to do it, I would back up all important data and do option 2 first (shrink partition 10 from the right, expand partition 11 to the left). It may very well work out fine, and it's done.  If not, use option 3.

ye ty for trying but i still need to figure out why gparted isnt working for me i hope oldfred will help me.

---

### Post by oldfred on 2017-05-12
You can only use gparted from live installer. Either Ubuntu live ISO or you can down load a gparted live ISO that you can create a live bootable flash drive.

If resizing the NTFS partitions use Windows tools. If resizing or moving Linux partitions use gparted or other Linux tools.

Your UEFI posts show UEFI fast boot on. That can make it tricky to get back into UEFI, normally while reconfiguring system best to have that off.
Not sure what your Secure Boot settings say or mean. One says Secure Boot disabled and other says it is Secure boot status is on? Is it really on or off?

I have Intel Virtual technology off. But not sure what it does.

---

