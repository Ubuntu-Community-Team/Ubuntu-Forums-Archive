---
title: "Getting past Windows bootloader"
date: 2018-05-06
forum: General Help
---

### Post by jdkcarlson on 2018-05-06
I am the author of this question:

[https://askubuntu.com/questions/1019519/defeating-windows-bootload-redux](https://askubuntu.com/questions/1019519/defeating-windows-bootload-redux)

Briefly, I have an Ubuntu partition installed on an originally Windows machine, but I can't manage to boot to it anymore. The advice that seems to have helped most people navigate similar issues

[https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432](https://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows/88432#88432)

doesn't seem to be working for me; I've been through the steps three times now. I have UEFI but not the separate partitions for /var et al. I'm not certain whether I'm somehow doing something wrong or there's some deeper issue with my system. If possible, I'd really appreciate some help diagnosing the problem and getting past it so I can access this partition again.

Thank you.

---

### Post by rohitsuman86 on 2018-05-06
Windows will not let you boot into windows but GRUB that comes with linux will let you boot into Windows or any other OS you have on this or any other hard drive on your system.

Also, to dual boot, you need both OS either installed in EFI mode or in Legacy mode. Also, if you wan to use certain drivers in Linux llike NVIDIA drivers, then install linux with "Secure Boot Off" in BIOS.

Windows and Linux EFI partitions need to be different. This is so, if you do any repair tool in related to EFI partition in windows, then linux will stop booting.

**SOLUTION :**

So, download and install EASEUS partition master in windows. See whether you have two partitions, one EFI partition for windows and another EFI partition for linux. You probably don't.

If not, then simply for delete linux partition using above mentioned software in windows and create two partitions.

One partition should be of 500 MB and another of whatsoever size you want to dedicate to Linux OS.

Then Install Ubuntu 18.04 again and while installing it, make the 500 MB partition as EFI System Partition (ESP) and Format it as FAT32 ONLY!!

Put mount point of "/" in your other partition and format it as EXT4. This will put your Linux OS in this partition. No need of SWAP PARTITION in UBUNTU 18.04

Install GRUB bootloader to the HDD in which these two OS exists.

That's it, you are done. When your system will start, GRUB menu will show up and in that windows boot manager will be listed. Using that menu, you can either start windows or Ubuntu anytime.

**Simplified Solution (Recommended):**

1) Disable UEFI support in BIOS or Enable Legacy Support.
2) Install windows 10 again in Legacy Mode as UEFI based windows 10 that's already installed will not work after disabling UEFI completely.
3) Make one separate partition for Linux, put mount point " / " on it and Install Ubuntu.

That's it. No need to make EFI partitions in UEFI mode. No Nvidia or other drivers problems as is in UBUNTU installed in UEFI mode with secure boot ON.

---

### Post by jdkcarlson on 2018-05-06
Hi, while I appreciate your effort, if I'm being completely honest, I'm not sure you've understood what I've written. 

I already have a Windows partition and an Ubuntu partition on the device in question. Unfortunately, GRUB is not working on my device. A well-regarded set of steps to reinstall it, linked in my original question, seem for unknown reasons to fail. I do not want to reinstall Ubuntu or Windows, or repartition my device. (At present I do not even have the disk that would let me reinstall Windows.) I want to recover my data from my existing Ubuntu partition and be able to access it again, not delete everything and start over. This is a set-up that had served me well and without incident for some time.

> This is so, if you do any repair tool in related to EFI partition in windows, then linux will stop booting.

This is not what has happened. I did not use any partition-related tool before the problem occurred.

> So, download and install EASEUS partition master in windows. See whether you have two partitions, one EFI partition for windows and another EFI partition for linux. You probably don't.

[This is what my partitions look like. ]("https://pasteboard.co/HjTu9ab.png")

> If not, then simply for delete linux partition using above mentioned software in windows and create two partitions.

No, this is nearly the opposite of what I am trying to do.

> One partition should be of 500 MB and another of whatsoever size you want to dedicate to Linux OS.

Again, it is not completely evident from this response that you have understood the nature of my question.

---

### Post by rohitsuman86 on 2018-05-06
Ok!!

1) I was just telling you the best practices to ensure that you will never get into this kind of soup again.

2) Your windows obviously deleted GRUB from EFI partition without you knowing about it, that's why Ubuntu doesn't show up upon pressing F12 key. 

3) But I do NOT recommend a single EFI partition because windows can do it again and I also recommended you to reinstall OS(s) in legacy **but it seems you don't want to do either of them.**

Here's the solution that you want :

[https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition](https://askubuntu.com/questions/831216/how-can-i-reinstall-grub-to-the-efi-partition)

*The solution that you want is on askubuntu only, *

---

### Post by yancek on 2018-05-06
The image you linked to in post 3 showing your partitions shows 3 windows partitions, 1 vfat EFI and 2 ntfs.  Shows another small (16MB) partition (empty) and another 217GB partition which also showss empty.  Was that your Ubuntu partition size?  One likely cause of this is a major update of your windows 10 as some of them will re-write the partition table and not include any non-windows partitions.  If that is the case, take a look at the link below, post #3 and review the links in that post for a possible solution.

  [https://ubuntuforums.org/showthread.php?t=2364091](https://ubuntuforums.org/showthread.php?t=2364091)

---

### Post by oldfred on 2018-05-06
Windows will not see data in Linux partitions, so may be ok.

Grub only boots working Windows. Or Windows that does not need chkdsk (after abnormal shutdown) or is hibernated.
And Windows turns fast start up back on with updates, so if you booted into Windows, it may have done updates and turned fast start up back on. Then grub will not boot it. 
Check that fast start up is off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html

      [/URL]
 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) 
    [URL="http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html"]
[/URL]

---

### Post by jdkcarlson on 2018-05-06
Sorry, I didn't see these replies. I was unsuccessfully trying to fix another problem all day.

Hi Rohit, I think I tried this answer before the other one, but I will try it.

yancek, the 217GB partition is the Ubuntu partition. It's not actually empty; I can boot via a thumb drive and mount the partition, and see all the stuff still around. 

I know for a fact I didn't authorize Windows to update anything. I think the partition isn't even big enough to support an update, but I wouldn't want it to anyway. As far as what it might do without my permission, though ... I'm not clear. I believe it may have tried. 

I don't exactly understand what you are saying: this Windows app knows about the partition (though it regards it as empty). Are you saying the problem might be that Windows doesn't know that the partition is there? (Would this be interfering with the GRUB reinstallation steps (which I've been through three times now) working, as outlined in the solution I linked in my initial post?) You said I should pursue the solutions you linked if I determine this to be the case; do you know what I could do to determine whether it's the case or not?

oldfred, I'll check the fast startup thing. Here is what Boot-Info says:
[http://paste.ubuntu.com/p/tJf42kM7xQ/](http://paste.ubuntu.com/p/tJf42kM7xQ/)

---

### Post by jdkcarlson on 2018-05-06
oldfred, I've turned off Fast Startup. The instructions say to reboot after this, but the only way to reboot Windows now, according to it, is "Update and restart," and I thought updating was something to avoid. How should I proceed?

---

### Post by yancek on 2018-05-06
Did you turn off automatic updates in windows?  My understanding is that with the Home Premium version (and possibly others) it is not possible to do.  It is only some major updates which will turn on fastboot without notifying you.  Your boot repair output does show that your windows is hibernated and you can't change that from Ubuntu.  Check any options in the BIOS and check the links posted by oldfred as he knows more about this than others here.

A default windows install will not do more than recognize there is a non-windows partition there.  You can't read or write to it without installing additional software so I'm sure your Ubuntu files are all there it is just the partition table which was changed.  You might be able to fix it with gparted or testdisk but I'm not really sure of the methods.  Might wait for another response or if you have your windows recovery CD you created when you first booted windows, you could try the repair option, see if you can run chkdsk.

---

### Post by yancek on 2018-05-06
Deleted duplicate post.

---

### Post by oldfred on 2018-05-06
Report shows it still is hibernated, or perhaps needs chkdsk.
Then Linux NTFS driver will not mount your NTFS partition and those are the two main reasons.

Both systems seem to be UEFI, but script could not even see the FAT32 ESP partition, sda1.
Normally script does see that. You may need chkdsk on sda1 or since FAT32 this from Linux.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

I see Acer, is this an Acer computer & what model?
Acer has a unique requirement of creating an UEFI password (never lose it, or remove it later) and enabling "trust" on the Ubuntu/grub .efi boot files from withing UEFI.
Many Acer & almost all computers need UEFI updates, for the KPTI/Retpoline changes for Meltdown/Spectre mitigation. Some older Acer threads may mention downgrading UEFI, but newer ones say update is better.


 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) 
      
 Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:

---

### Post by jdkcarlson on 2018-05-07
Hi yancek, it looks like your reply double-posted. I basically only ever access the Windows partition to troubleshoot if something is broken in Ubuntu and I hadn't known that this was a threat until it already kneecapped me. I've followed a few how-to links that suggest that modifying the registry in specified ways can stop this behavior, but it remains to be seen. I'll look at oldfred's links: the key point now is that I want Windows "unhibernated" to fix this?

I know my files are there, because I can see them when I mount the partition, but it'd be nice to be able to access them through the GUI and run programs in Ubuntu again. If things get really bad I can book through a USB stick and transfer all the files that only exist locally to an external HD, then nuke everything and repartition as Rohit suggests, but I'd really rather it not come to that.

I'd rather not run CHKDSK... ever . Apparently amongst the circle that deliberately runs Windows, it's also known as FCKDSK, for reasons I'll leave to your imagination. On an old Windows machine some five years ago, I once did run it on an external hard drive with a faulty checksum, only to have the contents scrambled irrecoverably. I still vaguely hope to watch some of those movies, someday...

---

### Post by jdkcarlson on 2018-05-07
Oh, hi, oldfred. Your reply was after yancek's and I didn't see it. I really wish the forum would notify users of each reply.

My machine is an Acer Aspire R14 R5-471T.

You've given me a whole lot of information and options; any idea what should I do first? My inclination is to first run the line of code you posted after booting from the stick. After that I'll look at some of the links in your previous post about defeating hibernation. Does that sound reasonable?

---

### Post by jdkcarlson on 2018-05-07
Actually, I take it back: I'm scared to reboot because my only option to do it through Windows is "Update and restart," whereas on the other hand if I just hold down the power button I lose whatever changes I just made asking Windows not to automatically update and turning off Fast Startup. First things first, what should I do with regard to this?

---

### Post by westie457 on 2018-05-07
Force stopping any OS is not a good idea.
Let Windows do the update and restart.
Then check and reset the 'Fast Startup' options to off. These settings are usually done in Control Panel > Power Options > Choose What the Power Buttons do > Check Options Currently Unavailable.
Reboot the system using a Live DVD/USB  and run Boot Repair using the Advanced Mode to reinstall Grub and set the OS to boot by default. Look at the options in the tabs..
After the Boot Repair if you can only boot into Windows check the Security Options in the UEFI settings page to enable 'Trust' on Ubuntu.


After doing all of this and you still do not get a Grub Menu (goes straight to Windows) do what is suggested at the end of your Boot Report.

Let us know how it goes.

---

### Post by oldfred on 2018-05-07
If you have any sort of abnormal shutdown you have to run chkdsk for NTFS or fsck for ext4 formatted partitions. And yes, if drive damage is the real issue, chkdsk may make it worse. Part of reason for really good backups as hard drives do fail.

You will still have to go into UEFI and set "trust" on the .efi boot files.

I have this in my notes, now older. I think I added the R14 as someone posted it also worked on their R14. And links above I know work as multiple users have posted they do explain trust.
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on Ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)

---

### Post by jdkcarlson on 2018-05-08
Hi all, I only had a little time last night to work on this, but today, I got it! 

I restarted Windows, and went to make sure the Fast Boot was still off. It was. I ran Boot-Repair with the options westie457 recommended, but it never finished, so I hit Ctrl+C. Then I ran it again. I realized then there was a GUI interface I'd forgotten about while I was waiting for it to run, so I can't be sure what went wrong, if anything. The second time I ran Boot-Repair it told me that I needed to clear space off this partition and also that I needed to turn Secure Boot off and run it again. When I rebooted, Windows bootloader still grabbed me. I went to turn Secure Boot off in BIOS (F2 on startup, on my machine), but I remembered that in the first link on "trust" that oldfred posted, Secure Boot needed to be on to mess with the "trust" settings. I set a password, and in the "trust" dialog told it to trust the three .efi's (MokManager, shimx64, and grubx64), assigned them names (I had to navigate through this three times; it wouldn't let me add more than one at a time), then moved them all past Windows Bootloader in the boot order. 

When I restarted, I had a normal looking list of options and was able to boot into Ubuntu again. Thank you all.

---

### Post by jdkcarlson on 2018-06-08
One last question for oldfred: do you agree with my first correspondent in this thread that there was something I should have done differently in my original partition? I'm about to run roughly the same process on a different laptop (turning off Windows automatic updates first) and wanted to make sure to avert catastrophe at the outset this time, if I had somehow been courting it before.

---

### Post by oldfred on 2018-06-08
it depends a lot if newer UEFI hardware or older BIOS only system.
And with UEFI you can install in the older BIOS mode for compatiblity, but usually want UEFI boot mode.
How you boot install media UEFI or BIOS is then how it installs.

See the "easy" 9 steps in link in my signature.  And then more links for anything you do not understand.

---

### Post by jdkcarlson on 2018-06-11
Thanks, oldfred! I'm starting this now, and I'm noticing something different than I did last time already. The Disk Management tool that comes with Windows is only letting me shrink the Windows partition to half the drive size, whereas in the past I've used a third-party tool to shrink it to some 30 or 40 Gb as per, for example, this link: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions). Is that not safe to do? I really don't want a Windows partition of any size, but just some small portion I know will still run even if some mishap completely lays waste to the Ubuntu partition. 

I can ask this in a different thread if that would be appropriate.

---

