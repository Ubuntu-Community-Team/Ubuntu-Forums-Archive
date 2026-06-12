---
title: "Not sure about Ubuntu partitions"
date: 2017-04-03
forum: General Help
---

### Post by a-lapsley on 2017-04-03
I am trying to have a machine with both Windows 10 and Kubuntu 16.10 available to boot. I had difficulty installing Kubuntu, so I had to try about 3-4 times, and now my hard drive is messy with partitions. I would like to clean it up, and also increase the size of the Windows partition as (for now) I intend on sticking to that as my main OS. From the attached Disk Managment screenshot, could someone please advise me on which partitions can be deleted? Or if this isn't enough information, how to go about finding it?

Thanks

[IMG]http://i.imgur.com/z2sUSK8.png[/IMG]

---

### Post by oldfred on 2017-04-03
Post these.
sudo parted -l
df -h

Windows has lots of required partitions.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Normal default Ubuntu install is just / (root) & swap. Many add /home or other data partitions. Back when I still had XP I also had a shared NTFS data partition for any files including Firefox & Thunderbird profiles that I might want in either system. 

But if you forced default install where it auto shrinks largest partition and adds new / (root), you may have gotten multiple installs, multiple roots.
Normally if reinstalling, you use Something Else and choose the existing / to reuse it.

this shows even a lot more info on all installs and boot configuration.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by a-lapsley on 2017-04-04
PasteBin for the results: [http://paste2.org/aN7Kt9sZ](http://paste2.org/aN7Kt9sZ)
This is the result of the two Linux commands:
[IMG]http://i.imgur.com/1Ksg2rf.png[/IMG]

---

### Post by oldfred on 2017-04-04
Only sda12 is a Linux partition. All the rest are NTFS or required Windows partitions.
You do show multiple 100+GB NTFS partitions. It looks like those may have been ones you made?

With terminal commands it is better to copy & paste, not use screen shots. But if long also use code tags.
And with screen shots better to attach than post in line.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[URL="http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098"]http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098
[/URL]
 How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168) 

Are you installing in UEFI boot mode?
[       ]("http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098") Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    [ ]("http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098")        Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

HP is not particularly dual boot friendly.

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

See also link below in my signature.

 Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by a-lapsley on 2017-04-04
I think that I did install Ubuntu in UEFI, yes.

I've had a change of heart regarding my setup, and I now want to completely uninstall Ubuntu, and remove all the partitions which are not necessary for Windows. Are these partitions the 100GB+ Primary partitions? And then the Recovery, EFI System and OEM partitions are the Windows required ones?

I'm not massively knowledgeable when it comes to OSs or partitions, so apologies.

---

### Post by oldfred on 2017-04-04
See post #2 for typical Windows UEFI based required partitions. But every system may be somewhat different.
Did you do a full backup of your system when you got it?

---

### Post by Impavidus on 2017-04-04
Partitions 8, 11 and 12 are Linux partitions, but your currently installed Kubuntu doesn't use partition 11. Partitions 1, 2, 3, 4, 5 and 6 were probably present before you began your installation attempts. Partition 7, 9 and 10 I don't know. They are Windows partitions. See in Windows if there's anything in them.

Keep in mind the partitions are not numbered in order, Windows lists them in a different order than Kubuntu and Kubuntu reports their sizes in GB and MB, but Windows in GiB or MiB (even though it says GB and MB). 1.0737GB=1GiB, 1.0486MB=1MiB.

---

