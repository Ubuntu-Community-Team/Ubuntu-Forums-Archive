---
title: "Failed to mount and see Windows from Linux"
date: 2016-05-21
forum: General Help
---

### Post by susja on 2016-05-21
[COLOR=#000000][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I have a laptop with one drive C: and Windows 7[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]I use systemrescuecd utility, boot and select default option.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Then I run:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]fdisk -l [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Then I see a list like this:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Device Boot Start End Sectors Size Id Type[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda1 63 2047 1985 992.5K 422 SFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda2 * 2048 616447 614400 300M 42 SFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda3 616448 260075519 259459072 123.7G 42 SFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]/dev/sda4 260075520 488395119 228319600 108.9jG 42 SFS[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Then I do the following:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]mkdir /media/windows[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]mount /dev/sda3 /media/windows/ [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]cd /media/windows[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]ls[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]And I see only:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]$RECYCLE.BIN and System Volume Information[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Then I try to mount /dev/sda4[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]And I see:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Boot bootmgr pagefile.sys Recovery $RECYCLE.BIN system.sav System Volume Information HP_WINRE[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]My goal is to access C: drive e.g. C:\Temp BUT I don't see it.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]My question: what I'm doing wrong and how to see Windows fs e.g. C: ?[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Thanks[/FONT][/COLOR]

---

### Post by X-RED_Tech on 2016-05-21
SFS means dynamic partitions, a Microsoft proprietary technology not supported in Linux.
In this case it's actually a good thing because it prevented the user from doing a potentially dangerous (for Windows) action. You shouldn't be writing to or even accessing the Windows system folders from other OS; Windows may require chkdsk in the next boot or not boot at all.

---

### Post by oldfred on 2016-05-21
Microsoft makes it easy to convert to dynamic partitions, but it is a one way process.

 Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm) 
   Several users have used this, it has a liveCD download to use but you have to use the non-free version:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529) 

Do not create partitions with Windows, but do use Windows to shrink NTFS partition(s) and reboot immediately so it can run chkdsk which is required after any resize.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by susja on 2016-05-23
Someone suggested to use ldmtool from ubuntu 16.04 because this utility should allow to see SFS.
Installed Ubuntu 16.04 and as soon as I started it it 'automagically' mounted all partitions including SFS hence I didn't need to play with ldmtool.
Hence this solved my problem.

---

