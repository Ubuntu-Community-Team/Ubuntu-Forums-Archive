---
title: "Win10 update crushed my dual-boot; is there any hope?"
date: 2018-01-19
forum: General Help
---

### Post by arekszklarczyk on 2018-01-19
Hi,
I've had a dual-boot system installed on ThinkPad430 for over a year and all was well and shiny (Win10 and Ubuntu 16.04).
Yesterday, I updated my Windows 10 and it choked, reverting to error message from GRUB.
I rebooted from a pen drive (Linux), updated boot-repair, run recommended repair.
I was happy for a moment since Windows finished its update and it works just fine, except I lost dual-boot starter window and access to Linux.

1) Is there any hope in recovering access to Ubuntu or data from it? Is it all lost, erased by Win10?
2) Since the accident I have read that the issue is well known!! So maybe the dual-boot is not such a smart thing to do, I simply followed recommendations from some learned people. Retrospectively,  I rarely used Win10, I was curious about this new flashy Cortana, also it was some sort of a known devil backup just in case Ubuntu, which I was totally new to, had issues with me or vice-versa; turned out Ubuntu is friendly and stable. Likely the problem will repeat itself with every major system update. Can you work around this issue? 
3) What is a reasonable way out of this mess? 

Best. Arek

---

### Post by oldfred on 2018-01-19
UEFI or BIOS?
If UEFI can you select Ubuntu from UEFI boot menu?
If BIOS, Windows update may have "forgotten" to include the Linux partition when it rewrites the partition table.

Also major updates to Windows 10 turns fast start up back on which is hibernation. So even if you correctly turned it off before you have to do it again.
And grub only boots working Windows, or Windows that is not hibernated nor needs chkdsk.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[URL="https://sourceforge.net/p/boot-repair/home/Home/"]https://sourceforge.net/p/boot-repair/home/Home/

[/URL]Lenovo boot screen can be accessed by Fn + F2 keys, boot device selection by Fn + F12 

Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by arekszklarczyk on 2018-01-19
Thanks. It is BIOS. I will look up this hibernation thing, I recall a message (when I was on Try Ubuntu) complaining about failure due to windows not being off or hibernating.

---

### Post by oldfred on 2018-01-19
If BIOS and only one drive, you only have one MBR.
Then when grub cannot boot Windows because of issues you have to temporarily reinstall a Windows boot loader to directly boot it and see if f8 gets you into repair console. Or you have to use your Windows repair/recovery flash drive.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

      
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html) 
    
      
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by arekszklarczyk on 2018-01-20
1. I disabled fast-startup on Win10 - no effect
2.  BootInfo summary report is here - [https://paste.ubuntu.com/26415700/](https://paste.ubuntu.com/26415700/)
3. from inside Windows I tried to look up Linux files  using Linux_Reader (tried two different tools out of 3 presumably up to the job) - it shows Linux Swap 7.73Gb, Unallocated(at end) 506Mb, Unallocated (in the middle) 90Gb and C: 124Gb NTFS, NTFS vol 1 100Mb, NTFS vol2 897Mb. I could not open more than that. The other tool ext2explore did not work at all. 

I will look up other suggestions.

---

### Post by oldfred on 2018-01-20
You have the classic Windows bug.
It forgot to write your Linux logical partition back into extended partition. And renumbered swap to sda5, but that is not critical. You can just add your partition back (probably as sda6, now) with parted rescue or testdisk and reinstall grub.

>  /dev/sda4         262,356,990   467,824,639   205,467,650   5 Extended
/dev/sda5         451,614,720   467,824,639    16,209,920  82 Linux swap / Solaris 



If only one Linux partition it starts two sectors after the start of the extended and ends a few sectors before the start of swap. 

       backup partition table before any changes, so you can get back to current if changes not correct
sudo sfdisk -d /dev/sda > PT_sda.txt
So you know sectors :
sudo parted /dev/sda unit s print 

      Used parted rescue
[https://ubuntuforums.org/showthread.php?t=2362656](https://ubuntuforums.org/showthread.php?t=2362656)
[http://ubuntuforums.org/showthread.php?t=2315405](http://ubuntuforums.org/showthread.php?t=2315405)

see
man parted
  >            rescue start end
                     Rescue  a  lost  partition  that  was  located  somewhere
                     between  start  and end.  If a partition is found, parted
                     will ask if you want to create an entry  for  it  in  the
                     partition table.

---

### Post by arekszklarczyk on 2018-01-21
Great!. It worked. Back to normal (except maybe bootloader screen color seems different).
I did exactly as you suggested. Thanks for helping. Below is a summary.

1. From Live Ubuntu (Try Ubuntu, on pen-drive) I looked up partition table, and wrote it down for reference:
   
$ sudo parted /dev/sda unit s print

partition 1, 2, 3 primary/ntfs (Windows10)
**partition 4** extended (this I need to reclaim)
partition 5 logical linux-swap(v1)

start of **partition_4** was at 262356990s; end was at 467824639s

2. I used parted rescue
  $ sudo parted
  $ unit s
  $ rescue 262356990s 467824639s
    Yes

3. run boot-repair

  sudo add-apt-repository ppa:yannubuntu/boot-repair
  sudo apt-get update
  sudo sudo apt-get install -y boot-repair && boot-repair

4. rebooted; dual-boot screen showed up as before

---

### Post by oldfred on 2018-01-21
Glad you got it working.

I might still back up your current partitions. If Windows does another major update, you may have same issue, but then can easily restore from backup.
see also 
man sfdisk

       sudo sfdisk -d /dev/sda > PT_sda.txt 
And copy to your back up drive or an external flash drive.

---

### Post by arekszklarczyk on 2018-01-21
Thanks. I may consider removing Win10 or reversing to Win7, I don't know, I spend most of my time in the browser. Best. A

---

### Post by oldfred on 2018-01-21
Windows 7 default installer is BIOS only and incorrectly converts a gpt partitioned drive to MBR.
But the Windows 7 installer can be converted to UEFI install by copying to flash drive and renaming/moving some files.

---

