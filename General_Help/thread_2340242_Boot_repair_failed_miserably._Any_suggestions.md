---
title: "Boot repair failed miserably. Any suggestions?"
date: 2016-10-16
forum: General Help
---

### Post by MibunoOokami on 2016-10-16
A few days ago I was informed that a PC I had installed Ubuntu on to dual boot with Windows 10 had some how lost its ability to give the option of which OS to boot into, it goes straight to Windows.
 
 
 Having looked at it today and spoken with the owner about what had happened, I’m to understand an unauthorised update occurred and removed the… Boot loader? I think that’s what it’s called.
 
 
 I booted it with a live CD, downloaded, installed and used boot-repair, did the pastebin just in case and rebooted. It went straight to Windows again, f12 offered no other optional OS to choose from. I used command prompt as admin and entered this command ```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
``` as per boot-repair’s suggestion. There was a message from prompt indication the command was initiated successfully and I proceeded to reboot only to now have no OS options and a message saying “reboot and select proper boot device or insert boot media in selected device and press any key”.
 
 
 Pastebin output is [here]("http://paste.ubuntu.com/23336700/"), I’m not experienced enough to be able to see any noticeable problems, unless there aren’t any. Can someone help me sort this out.
 
 
 Unfortunately my initial advice of buying an external HDD and backing up files went unheeded, the owner thought it was something that could wait… Hopefully there’s a way to fix this without losing any files etc? I don’t think it’s a terribly big deal if anything on windows is lost as it’s primarily used for a child to play educational games on.
 
 
 Thanks in advance for any further help you can provide.  
 
 
 P.S Secure boot is disabled due to UEFI system.

EDIT:   Boot-repair and manual grub-install failed on this system and I ended up being asked to do a factory reset before getting to the bottom of this problem. Hence marking it as solved.  
 There may be a potential solution in post [#15]("https://ubuntuforums.org/showthread.php?t=2340242&page=2&p=13559068#post13559068") by OldFred.

---

### Post by oldfred on 2016-10-17
Windows will reset itself to first in Boot order in UEFI on major updates or changes. Some have reported it likes to do it all the time.

Is Acer at newest UEFI for that system? Some threads say to downgrade UEFI but newer say to update to newest.
Is trust set for ubuntu/grub .efi files from UEFI.

If UEFI updated, perhaps trust settings lost?

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by MibunoOokami on 2016-10-17
> **oldfred said:**
> Windows will reset itself to first in Boot order in UEFI on major updates or changes. Some have reported it likes to do it all the time.

Is Acer at newest UEFI for that system? Some threads say to downgrade UEFI but newer say to update to newest.
Is trust set for ubuntu/grub .efi files from UEFI.

If UEFI updated, perhaps trust settings lost?

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 

[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

   Thanks for your reply OldFred.  
 
 
 I don’t know how to tell if UEFI is newest or not so can’t answer that question. As for trust settings, I’m not sure about those either. I followed the instructions in the links you posted but I don’t see any options to set boot mode to UEFI or to select a UEFI file.
 
 
 As mentioned above, I used admin command prompt to add the default ubuntu .efi file, perhaps it didn’t get set as trusted for some reason but it was after this that the machine won’t boot at all.  
 Looking through my notes when I installed Ubuntu, it was booting direct to Windows and the trouble shooting tips I read was to disable secure boot and to change said file, which worked successfully. I’m puzzled why the same steps won’t work this time. FWIW, f2 does nothing on the problem system, it requires delete key for BIOS. Or f12 just to change boot order.

 
 
 I’ll re-enable secure boot and then try boot-repair again to see if anything happens.

---

### Post by oldfred on 2016-10-17
While a different model Acer, you still should have screens like these.
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)

Somewhere usually in first UEFI screen is a version. And then you have to go to Acer's site and see if in Downloads or drivers they have a newer version.
You can add inxi program and it includes UEFI/BIOS version under machine.
sudo inxi -Fxz

---

### Post by MibunoOokami on 2016-10-17
Umm… My BIOS screen doesn’t look like that. When I’m in there under security tab there is only supervisor password (Installed), User password (not installed), change supervisor password [press enter], change user password [press enter] and security option [Setup].
 
 
 I’ve set the supervisor password again, nothing changed. Enabled secure boot and tried boot-repair but it said I have to disable secure boot first. Did so, got message saying repair successful reboot and got same message about selecting proper boot device.

---

### Post by oldfred on 2016-10-17
Then you may need to update UEFI from Acer.

---

### Post by MibunoOokami on 2016-10-17
I found [this]("http://www.zdnet.com/article/linux-multibooting-the-acer-aspire-z3-all-in-one/") rather large article, it makes me think that when I installed Ubuntu on the machine I may have erased the EFI boot partition. Although if I had, surely Ubuntu wouldn&#8217;t have worked on it in the first place or let me change the .efi file yesterday? There&#8217;s a small 200MB partition labelled Acer, but I can&#8217;t find a parent directory called EFI.
 
 
 From what I can tell, the UEFI is up to date.

---

### Post by MibunoOokami on 2016-10-17
I decided to try calling Acer for technical support, all they could offer was reset BIOS to default and when that didn&#8217;t work they suggested doing a factory reset.
 
 
 Here&#8217;s the [pastebin]("http://paste.ubuntu.com/23340952/") report from earlier, I forgot to add it to my last post. I just noticed the first line where it says there&#8217;s not boot loader installed  in the MBR of /dev/sdb which I&#8217;m guessing is the cause of my problems, not sure why boot repair didn&#8217;t add one. Also if I&#8217;m reading it correctly, the EFI files are still there somewhere. Hopefully this means work out how to re-install boot loader and things should be sweet.

---

### Post by MibunoOokami on 2016-10-18
Grub reinstall failed, there was an error message to the effect EFI file could not be found (I forgot to take a photo of message).
 It was suggested to use Gparted to find out which dev to install grub on which I had to do because the pastebin report lists everything as sdbX whereas it&#8217;s actually sdaX. Whilst there I found EFI partition under sda1, can only access it through terminal, tried following instructions in earlier post but no luck.
 
 
 I&#8217;m guessing there&#8217;s little other choice than to do a factory reset?

---

### Post by oldfred on 2016-10-18
With UEFI, there should not be a boot loader in MBR.
All boot files for all systems are in the ESP - efi system partition your sdb1. (not sda?)
Grub only installs in UEFI mode to drive seen as sda, so that may be part of issue.
Is this system use Intel SRT and have a small SSD for Windows hibernation? And that is sda, which is not then shown?

---

### Post by MibunoOokami on 2016-10-18
> **oldfred said:**
> With UEFI, there should not be a boot loader in MBR.
All boot files for all systems are in the ESP - efi system partition your sdb1. (not sda?)
Grub only installs in UEFI mode to drive seen as sda, so that may be part of issue.
 
 
 So the message about no boot loader can be ignored?
 
> **oldfred said:**
> Is this system use Intel SRT and have a small SSD for Windows hibernation? And that is sda, which is not then shown?
 
 
 According to the specs the system uses quad core Intel-i5. Not sure if SRT is something additional or not.  
 Whilst looking at the specs, I have just noticed the machine has half the standard RAM, so I wonder if it’s a faulty machine altogether. That may explain why an unexpected/unscheduled update happened and why after editing the .efi file to boot Ubuntu neither OS will boot.

---

### Post by MibunoOokami on 2016-10-18
Gparted definitely shows ESP being partition /dev/sda1. All the info is [Partition /dev/sda1; Name EFI system partition; File System fat32; Label ESP; Size 100MiB; Used 75.56MiB; Unused 24.44MiB; Flags boot, esp[/quote]
 
 
 Once again I tried installing GRUB below is the command I used and the output given
 ```
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:/# grub-install /dev/sda
 Installing for x86_64-efi platform.
 grub-install: error: cannot find EFI directory.
```
 
 
 When I mount sda1 in terminal and use ```
ls
``` it shows EFI directory and within that are > Boot Microsoft OEM and ubuntu

So I wonder why grub install can't find the EFI directory

---

### Post by oldfred on 2016-10-18
Your last summary report showed sdb1 as ESP, and no sda drive?

Grub will not install to an ESP on sdb.

If manually installing grub you need to mount the / partition first and perhaps other system partitions if separate.
Easier to use Boot-Repair in most cases.

---

### Post by MibunoOokami on 2016-10-18
> **oldfred said:**
> Your last summary report showed sdb1 as ESP, and no sda drive?

Grub will not install to an ESP on sdb.
 
 
 I don&#8217;t know what the story is or why there&#8217;s a difference between Gparted and the summary report as to where everything is. The report lists everything as sdb1-8 while Gparted shows everything as sda1-8.

> **oldfred said:**
> If manually installing grub you need to mount the / partition first and perhaps other system partitions if separate.
 
 
 When running some commands for manual install I initially mounted /dev/sda7 which should be root, I hadn&#8217;t mounted sda8 which should be home. When it comes to the actual install one of the commands said only need to use grub-install /dev/sda without a partition number and that&#8217;s when I get the error message about not finding EFI directory.
 Should I command grub to install on sda1 where the EFI directory is/should be? Or try installing it to sda7?

> **oldfred said:**
> Easier to use Boot-Repair in most cases. 
 
 
 Have tried that about 4 times now but nothing is happening. No errors but no fix either.

---

### Post by oldfred on 2016-10-19
There have been cases where the FAT32 partition is corrupted.
Either chkdsk or dosfsck (aka fsck.msdos and fsck.vfat)      usually fix it. A few have had to backup data, delete FAT32 partition. Then create new FAT32 partition with boot flag and restore boot data.

If seen as sdb1 change to that.
       sudo fsck.vfat -t -a /dev/sda1 
or:
      
 sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by MibunoOokami on 2016-10-19
The owner of this system asked me to go ahead and do a factory reset because they couldn&#8217;t wait any longer. Not knowing how to do this I phoned Acer again and they walked me through it&#8230; Only to find it wouldn&#8217;t reset either, they then said the warranty was void since another OS had been put on it and wanted to charge to fix it.
 
 
 Fortunately I was able download a free repair/installation tool from Microsoft, it couldn&#8217;t go back to a previous restore point perhaps because the machine is only about a month old. All other troubleshooting methods in the repair tool wouldn&#8217;t work so did fresh install it&#8217;s interesting to note that when doing the fresh install Windows went straight to the partition it was already installed on.
 After that I tried using boot-repair again and it failed miserable again taking me right back to the screen mentioned earlier > reboot and select proper boot device or insert boot media in selected device and press any key.
 
 
 Once again I started from scratch using the Windows repair tool, then re-installed Ubuntu (permission granted with scepticism) and had to use this command again ```
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi
``` now everything seems to be working just the way it was before that random update. It was a long process but I really would like to have been able to fix the problem instead of doing a fresh install. Hopefully it doesn&#8217;t happen again, I don&#8217;t think they&#8217;ll give Ubuntu a third chance.
 
 
 Thanks for you patience and assistance OldFred.

---

### Post by MibunoOokami on 2016-10-19
> **oldfred said:**
> There have been cases where the FAT32 partition is corrupted.
Either chkdsk or dosfsck (aka fsck.msdos and fsck.vfat)      usually fix it. A few have had to backup data, delete FAT32 partition. Then create new FAT32 partition with boot flag and restore boot data.

If seen as sdb1 change to that.
       sudo fsck.vfat -t -a /dev/sda1 
or:
      
 sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Hi OldFred,

You must've posted this while I was typing my long story. I'll take note of this in case the problem recurs. I ended up having to do a factory reset per the owner's request. 
I hate Windows so much...

P.S will mark thread as solved with a note.

---

