---
title: "Windows 7 kills grub every time it boots up !"
date: 2014-07-25
forum: General Help
---

### Post by qwerkus on 2014-07-25
Hello,

I've got a dual boot Desktop with both Ms Windows 7 and ubuntu 14.04 squeezed into an SSD, booted via UEFI and grub2 (when it goes well). Now every time I startup Windows, shut it down, and boot again, Grub2 menu loading fails with a very annoying "error: file not found.", and I have to use a live USB stick to repair it. The repair operation (mount, chroot, update-grub) works well, but becomes quite tiresome indeed. Somehow, windows always overrides the UEFI boot menu list. Is this a known issue ? Is there any workaround ? I know it's not our buisness to fix MS products; yet like so many others, I need it to run some crucial softwares for work; and it would be really nice if aftewards I could just switch back to my good ol' linux. So any Help would be greatly appreciated.

Here is the output of gdisk -l; 2 is /boot partition.

```
Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI System
   2          206848          411647   100.0 MiB   0700  Linux filesystem
   3          411648       126240767   60.0 GiB    0700  Microsoft basic data
   4       126240768       250069646   59.0 GiB    8300  Linux filesystem
```

---

### Post by oldfred on 2014-07-26
Generally better not to have a separate /boot partition for most desktops.

You are missing the system reserved Windows partition which may be part of the issue. And it has to be just before the NTFS partition on drive where you have /boot.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows 8 changes boot order often and we have to do work arounds to allow grub to boot. But Windows 7 typically has no issues like that.

Post link to BootInfo report. Do not run auto fix until we review things.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have two Ubuntu installs in my 64GB SSD. My 12.04 uses 11GB but my new 14.04 is not that large yet. But I have most data on my rotating hard drives.

---

### Post by qwerkus on 2014-07-28
Thank you for your helpful reply. I`m slowly digging myself through the ms documentation. In the meanwhile, to make room for an MSR partition, I tried to move the /boot partion to / (cp -r, reinstalled grub), but now efi doesn t seem to contain any infos an a linux partition anymore.

Anyway: here is the requested Bootinfo: [http://paste.ubuntu.com/7883015/](http://paste.ubuntu.com/7883015/)
Thank you for helping me out here.

PS: why is a separate /boot no a good idea ? Back to Freebsd and Gentoo times, when I started with opens source OS, everyone was all about a separated boot partition, which I must say came handy a few times, especially after a bad kernel compilation.

---

### Post by oldfred on 2014-07-28
You may have a grub.cfg in your /efi/ubuntu folder that is just a configfile to your boot. It may still refer to your old /boot partition and needs to be edited to be your / (root) partition where you now have boot.

Did you include -a in your cp command to preserve ownership & permissions. But I think all the kernels are owned by root. I have showing permissions on Nautilus and /boot kernels are in octal 100600. or just -rw? But others are 100644 or -rw-r--r-- and most of grub is also 100644.
see man cp

You show a grub in gpt's protective MBR for a BIOS boot but it is not correct. But it does look like you are now configured for UEFI boot as fstab has /boot/efi.
Your fstab still has both / & /boot, that would also need to be updated.

We regularly see users with full /boot, so the advantage of one partition for system files is that all space is shared. With servers, often RAID or LVM was not directly supported by grub legacy and you had to boot to load the drivers. Now grub2 does support those configurations, but servers may still want a separate /boot to protect kernels from rest of system. But maintenance to prevent partition from filling is required. That is expected that a server admin would know that, but often users do not do required maintenance/housecleaning. (oldfred goes off to do kernel housecleaning since he has not done that for a while). :)

---

### Post by qwerkus on 2014-07-28
Thank you for your reply. Files permissions were fine, but as Win 7 stubbornly refused to use the reserved partition I created, I gave it up, and went for a reinstall. My desktop needed the cleanup badly anyway. Sadly, I still got more or less the same problem: whenever I boot up Win 7, it somehow deletes grub. The only difference now, is that I don't even get a grub error, but rather directly the windows loading screen ! All the trouble of a clean reinstall for just nothing, how frustrating... Any new ideas are most welcome; here is a link to the new Boot-info: [http://paste.ubuntu.com/7888565/](http://paste.ubuntu.com/7888565/)

---

### Post by oldfred on 2014-07-28
What computer & model?
While often Windows 8 makes itself first, some UEFI just boot the entry with Windows and set that as first.

I have accumulated these alternatives. I suggest trying the rename of bootx64.efi first and see if you can set hard drive as first and have that stick.

       [http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
**Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
**a1**: Rename /efi/boot/bootx64.efi, copy shim or grub into /efi/boot and name it bootx64.efi  Then boot harddrive entry in UEFI menu.
**a2:**(this is the same as what Boot-Repair does in B:. 
Rename /efi/Microsoft/Boot/bootmgfw.efi and copy grub or shim into /efi/Microsoft/Boot and name it bootmfgw.efi  Then boot Windows entry to boot to grub menu. You have to manually add a grub menu entry to boot renamed Windows efi file. Grub2's os-prober entry boots bootmfgw.efi entry which is now just grub, so it will not work.

   Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu  with bkpbootmgr.efi entry
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair of bootmfgw.efi will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l " \EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by qwerkus on 2014-07-28
Wow, lots of stuff to check out. Yet I'm wondering: back in regular MBR times, I used to hack the windows bootloader to add a Linux entry. Looked pretty cool, and stopped windows from messing up my grub. Is something similar possible in EFI ?

My comp is no Laptop; just a desktop build upon an Asrock z77e-itx. The worst part is probably that at some point, it used to work. Than, either a grub,or a windows or a bios update made (part of) my life boring...

---

### Post by qwerkus on 2014-07-28
Just saw that your option C is something similar, and....

...it works (until now) !

As far as I understand it, bcedit forces windows 7 to check out grubx64.efi in order to find a boot manager. I guess I works as long as windows doesn't fancy rewriting the {bootmgr} path. How often would that happen ? What are my chances this workarounds screws something up - apart form loosing the sometimes useful windows boot options ?

---

### Post by oldfred on 2014-07-28
I always suggest that you have a repair CD or flash drive for the currrent version of every operating system you have installed.
Others have suggested the bcd edit version and I have not heard of any issues.

The main issue is that vendors are modifying UEFI to only boot Windows. And Windows 8 would alway reset itself on maintenance to be first in boot order. That may not be unreasonable, but with Windows 8.1 it resets on every reboot. Then it needs to be a user setting.

---

### Post by qwerkus on 2014-07-28
> **oldfred said:**
> The main issue is that vendors are modifying UEFI to only boot Windows.

This is totally unacceptable indeed. I'm wondering wether it would be enough to file a complaint at the european antritrust committe, as it appears this is the only authority currently able to scare Microsoft. I'm goint to ask my deputy. Anyway, a big thanks to you, oldfred, for your many helpful links. I just wont at least 15min/day! 

I don't know if it qualifies as 'solved', since it's more a workaround, but as long as it works for me... For the rest, the live-usb-whatever they call it these days has been my friend for a long time. Eh: sometimes, I take it the the local vendor's, and boot up an nice ubuntu on the display shelves - you gotta see those eyes :)

---

### Post by oldfred on 2014-07-28
Ubuntu has a policy statement.

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

And Microsoft years ago in a court case in Iowa showed its policy (back with DOS) was that they would not release software until it would not work with the competitor's DOS. It seems that still is their policy but I bet now they are smart enough not to have that in writing.

---

### Post by qwerkus on 2014-09-03
Update: Since I updated my bios to 1.90, the problem got partially solved. Now Windows still shows up on top of the boot list whenever it has been loaded, but it doesn't wipe out the UEFI boot list anymore. Thus I can still boot grub via f11 uefi boot menu, or manually put it as 1st boot option.  Progress, but not finished. Somewhere on the support forum, I read about the lack of secure boot option "corrupting" uefi boot list by forcing the load of ms windows. 1.90 seems to have corrected this on my asrock z99e-itx mobo.

---

