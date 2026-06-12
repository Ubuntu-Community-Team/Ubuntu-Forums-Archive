---
title: "Does your ubuntu support M.2 PCIe NVMe?"
date: 2022-01-15
forum: General Help
---

### Post by abdur7man on 2022-01-15
hi
I have a laptop and a PC.
I am trying to install my ubuntu beside windows 11
But the problem is that the M.2 PCIe NVMe disk does not appear until I install it next to Windows

What is the solution to this problem without losing Windows?

---

### Post by QIII on 2022-01-15
The machine I am on now is purely NVMe.  So that surely works.

Which machine are you trying to install Ubuntu on?  What do you mean by "But the problem is that the M.2 PCIe NVMe disk does not appear until I install it next to Windows"?

---

### Post by abdur7man on 2022-01-15
[https://www.msi.com/Laptop/GF63-Thin-10SCXR/Specification](https://www.msi.com/Laptop/GF63-Thin-10SCXR/Specification)
Laptop with two discs
the first  hard disk: [COLOR=#000000]M.2 PCIe NVMe[/COLOR]
The second  hard disk:  HHD
Windows is on the first hard disk.
When you request to install Ubuntu with Windows, only the first second hard appears

---

### Post by oldfred on 2022-01-15
Many have needed UEFI & NVMe firmware updates. 
Check both your system and your NVMe drive for newer versions, even if new system.

You do have to have drives in AHCI mode, but not sure if that matters with NVMe drives. But have to install AHCI driver into Windows first.
You need Windows fast start up off.
Often easier with UEFI Secure Boot off, but not sure with Windows 11.
But if you need proprietary drivers bit more complicated to install proprietary drivers like for nVidia, if you have that.

More UEFI info in link below in my signature.

---

### Post by abdur7man on 2022-01-15
> **oldfred said:**
> Many have needed UEFI & NVMe firmware updates. 
Check both your system and your NVMe drive for newer versions, even if new system.

You do have to have drives in AHCI mode, but not sure if that matters with NVMe drives. But have to install AHCI driver into Windows first.
You need Windows fast start up off.
Often easier with UEFI Secure Boot off, but not sure with Windows 11.
But if you need proprietary drivers bit more complicated to install proprietary drivers like for nVidia, if you have that.

More UEFI info in link below in my signature.

I don't know why all these complications.
The programmers of this distribution and other distributions are supposed to deal with users as ordinary users who are not professionals.
  As long as the issue is this difficult, I prefer to stay on my current system.
I really needed to try out the Linux system and learn it. But I didn't know it was that difficult.
Looks like I have to buy another laptop and make it Linux

---

### Post by jeremy31 on 2022-01-15
I wonder if some BIOS RAID is active and that is why Ubuntu doesn't see it but it is in Windows.

---

### Post by abdur7man on 2022-01-15
> **jeremy31 said:**
> I wonder if some BIOS RAID is active and that is why Ubuntu doesn't see it but it is in Windows.

There is no RAID system in the device
Each disc is independent of the other
However I can not install the system
It seems that the system with is not compatible with this type of device.
  I'm still surprised by this complexity of the user. The system is supposed to accept any device without annoying requests
Not the only device that I could not install the system.
I have a Custom PC Build  with the same problem. I have another laptop from hp, the same problem.
They all contain a hard disk [COLOR=#000000]M.2 PCIe NVMe[/COLOR]
All disks appear except for the M2 hard disk that has the Windows system, which did not appear

---

### Post by oldfred on 2022-01-15
I have no Windows on this system.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo nvme -list [/COLOR]
[sudo] password for fred:  
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev   
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- -------- 
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         188.18  GB / 500.11  GB    512   B +  0 B   2B2QEXM7


[/FONT]
```

All user whether Windows or not should be updating UEFI & firmware as standard security practice.
Spectre virus, repoline firmware update
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 

And changing a few settings is not unusual. The vendors design system for Windows and do not care about anything else.

---

### Post by abdur7man on 2022-01-16
> **oldfred said:**
> I have no Windows on this system.

```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo nvme -list [/COLOR]
[sudo] password for fred:  
Node             SN                   Model                                    Namespace Usage                      Format           FW Rev   
---------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- -------- 
/dev/nvme0n1     S4P2NF0M514514L      Samsung SSD 970 EVO Plus 500GB           1         188.18  GB / 500.11  GB    512   B +  0 B   2B2QEXM7


[/FONT]
```

All user whether Windows or not should be updating UEFI & firmware as standard security practice.
Spectre virus, repoline firmware update
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 

And changing a few settings is not unusual. The vendors design system for Windows and do not care about anything else.

UEFI has been updated
The same problem can not read
[IMG]https://file.an-island.net/uploads/164232929595581.jpg[/IMG]

---

### Post by oldfred on 2022-01-16
Always best to use Windows tools to shrink NTFS partitions & reboot so it can run required chkdsk.
While gparted/installer can resize NTFS, very occasionally there is an issue and then user blames Linux. Most often the issue was a pre-existing issue with the NTFS.
Do you have Windows fast start up which sets hibernation flag off?

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by tea for one on 2022-01-16
> **oldfred said:**
> Always best to use Windows tools to shrink NTFS partitions & reboot so it can run required chkdsk.
While gparted/installer can resize NTFS, very occasionally there is an issue and then user blames Linux. Most often the issue was a pre-existing issue with the NTFS.
Do you have Windows fast start up which sets hibernation flag off?

After you have followed this good advice from [COLOR="#0000FF"]oldfred[/COLOR]:- 

Do you have any sort of encryption on the nvme drive?
Any Intel Optane applications?

Ubuntu can definitely be installed on nvme drives as detailed in my PC
```
edited@edited:~$ inxi -D
Drives:
  Local Storage: total: 344.68 GiB used: 114.05 GiB (33.1%) 
  ID-1: [COLOR="#000080"]/dev/nvme0n1[/COLOR] vendor: Kingston model: SA2000M8250G size: 232.89 GiB 
  ID-2: /dev/sda vendor: SanDisk model: SDSSDHII120G size: 111.79 GiB 
edited@edited:~$ 
```
Possibly, something within Windows or even the UEFI firmware is causing the dilemma.

In post no. 7, you mentioned that you have a total of three computers, all with the same problem.
Are the nvme drives from the same manufacturer?

---

### Post by tea for one on 2022-01-16
In Post 9, is the image from the new Ubuntu installer for 22.04?

---

### Post by abdur7man on 2022-01-16
> **oldfred said:**
> Always best to use Windows tools to shrink NTFS partitions & reboot so it can run required chkdsk.
While gparted/installer can resize NTFS, very occasionally there is an issue and then user blames Linux. Most often the issue was a pre-existing issue with the NTFS.
Do you have Windows fast start up which sets hibernation flag off?

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

The device has no problem
   Yes, I blame Linux on
Three devices did not work on these requests.
Delete, edit, deactivate, and so on from the modifications for installation.
  Users are supposed to be treated as ordinary users who are not professionals and geniuses.


The device does not have any technical problem even the updates you requested were done and the same problem.

---

### Post by abdur7man on 2022-01-16
yes  

Looks like I'm going to buy a new laptop and customize it for LinuxSo that I do not lose my files and my Windows system in the current mobile

---

### Post by TheFu on 2022-01-16
On a PC - Ryzen 5600G with a B450 motherboard:
```
$ inxi -D
Drives:    HDD Total Size: 32826.5GB (72.7% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_970_EVO_500GB size: 500.1GB
...
```
I didn't do anything special for the nvme to be seen. It was just there.

Three are 8 storage devices connected to the system. No Windows anywhere. No EFI booting.  I use LVM and have a separate /boot/ partition.
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-root                  ext4  101G   61G   36G  63% /
/dev/sda2                                   ext2  237M  195M   30M  87% /boot
...
```

Which kernel is being use in your setup?  I'm not using the stock 18.04 5.4 HWE kernel because I wanted the Ryzen GPU supported. That needs 5.11.x or later (I think).

---

### Post by abdur7man on 2022-01-16
> **TheFu said:**
> On a PC - Ryzen 5600G with a B450 motherboard:
```
$ inxi -D
Drives:    HDD Total Size: 32826.5GB (72.7% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_970_EVO_500GB size: 500.1GB
...
```
I didn't do anything special for the nvme to be seen. It was just there.

Three are 8 storage devices connected to the system. No Windows anywhere. No EFI booting.  I use LVM and have a separate /boot/ partition.
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--vg-root                  ext4  101G   61G   36G  63% /
/dev/sda2                                   ext2  237M  195M   30M  87% /boot
...
```

Which kernel is being use in your setup?  I'm not using the stock 18.04 5.4 HWE kernel because I wanted the Ryzen GPU supported. That needs 5.11.x or later (I think).

 
I am neither a developer nor a programmer
  I am a normal user.
  This is my first use of Linux and I am not good with Linux terminal 
  Some say I am a normal user and and and in the end it turns out the opposite.
It seems that Linux and its distributions are not suitable for the average user and are not directed at them.
And finally they complain about the lack of users, make it popular for the average user

---

### Post by deadflowr on 2022-01-16
> When you request to install Ubuntu with Windows, only the first second hard appears
Choose the something else option.
When you select the option to install side by side it expects and sets it to install on same disk as other OS is on.

---

### Post by abdur7man on 2022-01-16
> **deadflowr said:**
> Choose the something else option.
When you select the option to install side by side it expects and sets it to install on same disk as other OS is on.

I mentioned in my previous replies when asking to install Linux alongside Windows, the installation does not take place on the same disk in which Windows is located because the system cannot read the hard disk in which Windows is located.

---

### Post by TheFu on 2022-01-16
> **abdur7man said:**
> I am neither a developer nor a programmer
  I am a normal user.
  This is my first use of Linux and I am not good with Linux terminal 
  Some say I am a normal user and and and in the end it turns out the opposite.
It seems that Linux and its distributions are not suitable for the average user and are not directed at them.
And finally they complain about the lack of users, make it popular for the average user

Welcome.  Normal users find that Ubuntu and other similar OSes are great for their needs.
Installing an OS is normally not done by typical users. How many people install Windows themselves?  Perhaps 10%?
I use to try to get more users on Linux, but after about 10 yrs, decided that wasn't my job. Use whatever works for you.  I do recall an extremely steep learning curve when I moved from mainframes to Unix and to PCs.  

Changing to a different OS is not easy, regardless of the new OS. There is always a steep learning curve.  Whatever OS was used previously, you probably had many years using it and learning. Expect the same for any new OS.  You may have been surrounded by other people running that other OS every day too. That meant is was easy to get help since the person next to you probably knew the answer. If you lived in a family all running Ubuntu, then your experience would have been different. 

Can you imagine a Linux-only user trying to install Windows for the first time?  What do you mean that I need a driver disk and I'm supposed to download GPU drivers from a vendor?  That's crazy. They should all be included with the OS already.  After it is up and running, there's a huge different in maintenance. With Linux, patching is 1 command, managed by the OS. This gets all the updates for 3rd party applications. No need to hunt down setup.exe files for each vendor.

It is all a matter of perspective.

**Another alternative:**
We don't actually need to dual boot. You can run a virtual machine and having both Windows and Linux running concurrently on the same system.  This is actually much safer, since there won't be fights between the OSes for which controls the boot files.  I've been running virtual machines since around 2006. Initially, it was Linux VMs on a Windows machine, but since 2010-ish, it has been Windows inside a VM on a Linux host. I haven't dual booted since around 2010.

---

### Post by QIII on 2022-01-16
If you have Windows on your NVMe device and its partitions take up the entire device, then you will not be able to install any Linux distribution on that device.  This is not a "programmer level" thing for Linux users.  It is a matter of using Windows to shrink its own partitions to make room for Linux.  ***Windows*** is more likely your problem than Linux if you are trying to install Linux on the same device.

You will need to use Windows tools to make room for Linux to install to.

If you think it is too difficult for "normal" users, millions of whom use Linux and even dual boot, then use what works for you.  We don't score points for converting Linux proselytes.  Nobody here makes any money off of this.  We are all volunteers and we don't work for Canonical -- the distributor of Ubuntu.

If Windows serves you, by all means use it and stop banging your head against a wall trying to install Linux.

Our editorial philosophy here:  Use what works.

---

### Post by TheFu on 2022-01-16
> **QIII said:**
>  You will need to use Windows tools to make room for Linux to install to.

If a storage device is full of other OSes, then Linux cannot use it.  Linux cannot be installed into NTFS file systems. That's a Windows-only file system.  Linux supports many other file systems, which can seem odd to Windows people. There must be 20 file systems used by lots of Linux people, but there are really 4 that are very popular AND meet the requirements for booting Linux.  NTFS is NOT in the list.

You can use gnome-disks to see the storage or you can run a terminal program to show everything. We tend to use terminal commands here because they work for any Linux release/flavor and they are concise.  In 1 line, I can ask for all the information, without having to type out 10 lines of point-n-click steps.
There are multiple ways to provide the information:

A) 
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint
```
This command will show the storage inside a system and the file systems and where empty space is located:
If you boot into a "Try Ubuntu" environment, run that command, then copy/paste the TEXT back here, and wrap that pasted text in "code-tags", we'll know what your systems has.

B) Run the **boot-info** tool which will provide the same information and much more. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

C) Run the **System Info** tool: [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

Both those last 2 will ask if you'd like the output to be pasted online and you will be provided an anonymous URL that will be available for 7-30 days. These are probably easier since they can be run from a GUI.

---

### Post by DuckHook on 2022-01-16
> **abdur7man said:**
> It seems that Linux and its distributions are not suitable for the average user and are not directed at them.
And finally they complain about the lack of users, make it popular for the average user
This is the fourth or fifth time that you have repeated this refrain.

Please note the following:

[LIST=1]
[*]Microsoft designs its operating system on purpose to make it as difficult as possible to dual boot another OS beside it. This is not Linux's fault. Blame Microsoft.
[*]Computer makers design their computers on purpose to only boot Windows without allowance for other operating systems. This is not Linux's fault. Blame your computer manufacturer.
[*]Users who want to dabble in Linux have unrealistic expectations that overcoming the above restrictions should somehow be "easy". This is not Linux's fault. Blame unrealistic users and silly expectations.
[/LIST]
If you want an easy Linux experience, then buy a computer that has Linux preinstalled. This will give you the same "easy" experience that you got when you bought your Windows computer. If you then want to install and dual boot Windows onto that computer, well, good luck. Windows has **NO** option that allows you to install it alongside something else. It will just hog your whole disk, wipe it clean, and install itself as the only OS.

So, if you want to fairly compare the two processes, think about the above instead of griping about Linux.

Lastly, it must be said: Linux is not for the "average" user and has no wish to be "popular". Nor does anyone "complain" about it's lack of popularity except—as far as I've ever seen—uninformed Windows users. It is for those who have made a *commitment* to learning something new and more powerful, flexible, empowering and safer. Many people who fit this description may only have "average" computer skills, but they are not average people in the sense of being common run&#8209;of&#8209;the&#8209;mill users (those stick with Windows). If you truly want to use Linux, your difficulties will not just end with the installation: you will be challenged further when you try to do anything beyond the simplest computing tasks. If you are not prepared for a learning curve and some challenges and discomfort, then my best advice is to forego Linux and stick with Windows. See the link in my sig: Linux Is Not Windows.

---

### Post by abdur7man on 2022-01-16
It is possible to delete the topic if it bothers you and does not provide benefit to the followers of the site  .

---

### Post by DuckHook on 2022-01-16
> **abdur7man said:**
> It is possible to delete the topic if it bothers you and does not provide benefit to the followers of the site  .
Au contraire. This thread has great benefit preparing general readers to approach a Linux install with realistic expectations. As for whom is bothered, I'm not the one singing the same old song four times.

The users on this forum have given you some valuable technical advice. It's your call whether you choose to embark on this journey. FWIW, I hope that you do. It's actually a grand adventure. But only if you are prepared to face some hardship along the way.

Good Luck and Happy Ubuntu-ing (if you so choose).

---

### Post by abdur7man on 2022-01-16
This is my first reply after installing Ubuntu alongside Windows.
The solution was to free up free space
desktop picture :
[https://imgur.com/7qVgYdD](https://imgur.com/7qVgYdD)

---

