---
title: "Read NTFS Partitions After Windows Kaputs"
date: 2007-05-03
forum: General Help
---

### Post by Gibran on 2007-05-03
Hello everyone,
I am dual-booting Feisty and XP, for some reason XP decided to give me the BSOD before even loading and restarting instantly (I can only catch a glimpse of said screen) and I've really had it with Ruindows, I think I'm going 100% Linux. Now, the problem is that since the system did not close properly my other NTFS partitions are not mounted and I can't access the info on them. I have a new hard drive I will add precisely to reformat everything to ext, but I can't without accessing my data on the NTFS drivers.  How can I mount the partitions again from Linux? is there a way to check them for errors and boot them from here? Thank you.

---

### Post by aysiu on 2007-05-04
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) is a good place to start. Post back any questions or problems you're having.

---

### Post by Gibran on 2007-05-04
When I try to mount the partitions it tells me:
> $LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS logfile is unclean. Choose one action:
   Boot Windows and shutdown it cleanly, or if you have a removable
   device then click the 'Safely Remove Hardware' icon in the Windows
   taskbar notification area before disconnecting it.


After I try ntfsfix it tells me I need to run chkdsk because the filesystem is corrupt... I think I might just install Windows again even if just to shut it down, LOL. My fear lies on the overwriting of GRUB (I've already had 2 Linux migration attempts foiled because of an XP reinstallation). Is there a way to install Windows without overwriting GRUB, or a way to reinstall without too many headackes? If not I guess I'll just take the hard drives and plug them into another PC just to shut them down :(  Thanks again!

---

### Post by aysiu on 2007-05-04
Before doing a reinstall, try this:
[HOWTO: Restore Lost Partitions to a Deleted or Corrupt Partition Table](http://ubuntuforums.org/showthread.php?t=370121)

---

### Post by Gibran on 2007-05-04
Thanks again, I was able to fix them somewhat so that I can force-mount the partitions now, but when I add my new hard drive it's on read-only, even though I just formatted it to EXT3, and to mount it I have to type the root password "for security reasons". How can I make Ubuntu recognize my new HD as it normally would? What I plan to do is copy the NTFS files to the new drive and format them to EXT3 (and thus ridding myself of anything Windows on my PC). Thanks yet again!

---

### Post by aysiu on 2007-05-04
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by Gibran on 2007-05-04
Thank you very much! I am now in the process of transferring the data from the last HD into the newly-created partition such warm and fuzzy feeling, to leave Windows for good (I hope!). I have bookmarked that page, excellent resources :) As a final question, how can I remove GRUB from the startup now that I no longer need it? (An poking around was really fun, learned something new today!)

---

### Post by aysiu on 2007-05-04
You don't need Grub?

---

### Post by Gibran on 2007-05-04
Well, since I don't need to choose between XP and Linux anymore I figured I wouldn't need it. I'll just set the timeout to 1 second if it cannot/should not be removed. Thanks a whole bunch for your patience **aysiu** :KS

---

### Post by aysiu on 2007-05-04
You still need a boot loader, even if you're not dual-booting. You can even set the timeout to 0 if you have a live CD handy for rescue purposes should anything go wrong.

---

### Post by kleam on 2007-05-04
ATTN: Gibran

Although it seems liek you have already solved your problem and have began your epic quest to convert to linux like many other whom have paved that path, BUT 

I think it vital for you to fix your windows.

Unless you are super-savy in the was of the penguin, It's always good to have an operating system that does not require any manual terminal use to use. Also Windows XP is very compatible with almsot everything. 

If you would like I know how you can fix your Windows XP operating system. 
IT IS ALWAYS GOOD TO HAVE A BACK-UP, and it doesn't make you less of a man to be 95% Linux. 




So you say that the system32 is corrupt.
Usually in a windows world this means that one of the crutial system32 files have been deleted, or a malfunction somewhere has caused one of the files to lose some information.

I Would suggest: 
1. pop in your windows xp cd
2. Change your BIOS to boot from CD then yoru Hard Drives
3. when the Windows XP Installer comes up find the key that says "repair"
---You will then have two options
----------Both will get the job done
--------------one will give you a repair command line
--------------one will run a diagnostics and replace any changed system files
4. I suggest going to the command line and typing 
'CHKDSK /R'
5. This should repair any system file problem you were having with your boot.
6. If this does not work, change the Directory ('cd') to the cd drive
7. The crucial files for windows xp to load are the "boot.ini, NTLDR, and NTDETECT.COM"
8. In a i386 folder of the windows cd you will find the files NTLDR and NTDETECT.COM
9. You want to copy those fiels to your root of your NTFS harddrive
----Note: Not %systemroot% but the actual root
-------If you installed on the c:\ drive put it right there
10. if you don't know the command to copy I have the command writen below:
'xcopy ntdetect.com'
'xcopy ntldr'


Of course if you are just fed up with windows xp, then I guess it is your choice. 

Be careful it could always be a hard-drive going bad

-Kleam

---

### Post by Gibran on 2007-05-04
Thanks for the tip, Kleam BUT...I already deleted all my partitions and I've been dual-booting for around 3 months now, so I think I've had every major problem I'll have and thanks to the excellent community I have sorted them all out. I do basically all of my tasks with Linux apps already, though I'll miss:

-Photoshop (There's GIMP, but I guess I'll have to get used to it, now)
-Custom Emoticons from Windows Live Messenger :lolflag: 
-Not having to place my webcam upside down to get the right display

However, I would like to know how to reinstall Windows without destroying Linux, should it be necessary.

---

