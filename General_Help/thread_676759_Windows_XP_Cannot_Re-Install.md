---
title: "Windows XP Cannot Re-Install"
date: 2008-01-24
forum: General Help
---

### Post by pieter346 on 2008-01-24
Well, I previously had an OEM copy of Vista on my computer then about two nights ago I installed Ubuntu and wiped EVERYTHING from the hard-drive.  This was mainly a test to see if I liked Ubuntu or not since I had my copy of XP lying around (since Vista is lame anyways)


So anyways heres my problem.   After re-formatting my drives again to NTFS and I re-boot with the XP install in the drive, right before it goes into the Windows partitioner I get a BSoD with the Error:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this Stop error screen, restart your computer.  If this screen appears again, follow these steps:

Check for viruses on your computer. Remove any newly installed hard drives or hard drive controllers.  Check your hard drive to make sure it is properly configured and terminated.  
Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical Information:

*** STOP: 0x00000074 ( 0xF78D2524 , 0xC00034 , 0x00000000 , 0x00000000 )

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Now I've tried almost every other suggestion, but I know for a fact Ubuntu caused this error.  My hard drives are fine and there are no viruses.

I hope someone can help me with this.  I just want Windows back (for compatibility issues) because Ubuntu has given me nothing but nightmares and stress

---

### Post by wjp.reg on 2008-01-24
What did you use to reformat the hard drive?

Most likely you need to use fdisk to remove/setup partitions.  I would leave your hard drive in an unformatted state and let the installer do the rest.

good luck

---

### Post by housam on 2008-01-24
If you'll go to reinstall win-xp again, I recommend to reformat your HDD with Partition magic tool.

---

### Post by bolucpap on 2008-01-24
Also, you may want to have a look at this article:

[http://support.microsoft.com/kb/326679](http://support.microsoft.com/kb/326679)

It may be that Ubuntu did not cause this error, your installation of Ubuntu and hardware failure may have coincided.

---

### Post by c0met on 2008-01-24
What I'd do is to boot your computer from the Ubuntu Live CD. 
[LIST]
[*]Under System >> Administration select the Partition Editor. This will show you the partitions and their formats. 
[*]Right click on each partition and select delete. 
[*]Do this to all partitions. 
[*]Now click on "apply" to process the changes.
[*] It's possible the Partition Editor will close down doing this. If that happens, simply restart it and make sure that the changes have been applied. They should have been.
[/LIST]
You will now essentially have an unformatted, unpartitioned hard drive that should be able to processed by you XP disk.
[B][COLOR="Red"]
PLEASE NOTE:[/COLOR][/B] What I have suggested you do will remove EVERYTHING on you drives. Please don't do it if there are things you need to keep.

LASTLY, the below link has some information on uninstalling Ubuntu that might be useful.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by pieter346 on 2008-01-24
> **c0met said:**
> What I'd do is to boot your computer from the Ubuntu Live CD. 
[LIST]
[*]Under System >> Administration select the Partition Editor. This will show you the partitions and their formats. 
[*]Right click on each partition and select delete. 
[*]Do this to all partitions. 
[*]Now click on "apply" to process the changes.
[*] It's possible the Partition Editor will close down doing this. If that happens, simply restart it and make sure that the changes have been applied. They should have been.
[/LIST]
You will now essentially have an unformatted, unpartitioned hard drive that should be able to processed by you XP disk.
[B][COLOR="Red"]
PLEASE NOTE:[/COLOR][/B] What I have suggested you do will remove EVERYTHING on you drives. Please don't do it if there are things you need to keep.

LASTLY, the below link has some information on uninstalling Ubuntu that might be useful.

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")


The thing is I have formatted both of my internal hard drives using GParted.   It still hasn't solved the problem.

But I will read the few links here and see if they help.

---

### Post by pieter346 on 2008-01-24
Nope.   Links haven't provided a solution

---

### Post by c0met on 2008-01-25
The suggestion that I outlined about was not about formatting drives so that they are ready for XP. I was suggesting that you use GParted to remove all formatting so that XP is presented with an unformatted disk. It might be worth a try.

Good luck.

---

