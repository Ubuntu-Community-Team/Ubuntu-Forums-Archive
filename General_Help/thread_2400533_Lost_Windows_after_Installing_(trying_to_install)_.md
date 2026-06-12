---
title: "Lost Windows after Installing (trying to install) Ubuntu"
date: 2018-09-07
forum: General Help
---

### Post by lmangiac90 on 2018-09-07
I desperately need your help with this:
1) Before this mess started, I was running two HDs (500gb<--Windows 7 on here, and 1tb<--- storage).

2) After repartitioning my 500gb to 398 gb to install ubuntu on the difference (~100gb drive, which I formatted to G::) I went ahead and tried to install ubuntu.

3) After getting an error during installation, the computer restarted and now windows won't load, or well, it will, as in it can get to the recovery options, but from there it doesn't find any windows, so it is of no help. I tried using my recovery CD, and it loads, but doesn't recognize any OS on the PC so it doesn't let me execute recovery.

4) Now I got really scared, and thought I lost my 500Gb (now 398gb) drive. However, I booted into the ubuntu live USB trial, and saw my 398 gb drive and my 1tb drive there with all of their files inside. I tried running boot repair on ubuntu and it did not help.

5) When I go into windows repair and try to select "load drivers" I see that I can search through my 1tb drive, but my 500gb drive does not show up. Why is that? Why is it recognizing my 1tb drive but not the 500gb drive where windows was installed on? Even when I try to install windows 7 from the repair CD on any drives, only the 1tb drive shows up, so it looks like when I was installing ubuntu on the 500 gb (398/102gb) drive, somehow the drive got reformatted to where its not being detected maybe? My BIOS shows both drives, fortunately.

What can I do? What happened to my windows 7? Is there any way to fix this? I have the following data from the boot repair software on ubuntu:
[http://paste.ubuntu.com/p/zcpVqptwkx/](http://paste.ubuntu.com/p/zcpVqptwkx/)

From GParted (with the 500gb drive selected): [https://ibb.co/fQemsp](https://ibb.co/fQemsp)

Also, nothing ever installed on the ~100gb partition I created specifically for ubuntu. Please help!

Ps. when I run my 500 gb(398gb) drive, it starts loading windows for a second and then it BSOD on me. I've had this problem before with the GRUB loader that I fixed by running the windows repair CD, but this is different as I did not even download GRUB or any ubuntu files it seems.

Solutions I've tried so far: [Recover Windows after reinstalling Ubuntu]("https://askubuntu.com/questions/463724/recover-windows-")...
(i.e. the Boot into the Windows installation media you borrowed or created. Choose the recovery "Advanced Options" until it offers you a command prompt or shell. I'm not sure if you want "bootrec /fixmbr" or "bootrec /fixboot)

THINGS IVE TRIED AND THAT WERE DISCUSSED ON ASK UBUNTU UNTIL THEY CLOSED THE HELP THREAD :(


[LIST]
[*]After you repartitioned the 500Gb and before trying to install Ubuntu, did you reboot and verified that Windows was still working? &#8211; [Aug 29 at 9:20]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1754897_1069945")
[*]Good question. I can't remember with absolute certainty either way, but I don't think that I did. &#8211; [Aug 29 at 22:46]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1755403_1069945") 
[*]After you make a backup, try installing Ubuntu again from a reliable USB to sda5. Install GRUB when it asks and you will probably be OK. Your issue seem to be due to the installation process fail. &#8211;  [Aug 30 at 10:42]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1755685_1069945")

[*]Thank you Katu, I'll try. Why is it that installing ubuntu is so difficult in the first place. Is there a good website out there with step-by-step instructions? I don't quite get this whole "/" and then "root" etc. Why can't I just choose my partition and have ubuntu take care of the rest. &#8211;  [Aug 30 at 13:28]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1755803_1069945")  

[*]Also, the screenshot of GParted I posted, just for clarification, is not correctly showing the status of my 500(398gb) drive. It was more than 70% used, meaning that out of the 500, 320 gb or so was used up. The remainder (180gb) I split into two and one of the halves if where I wanted ubuntu to end up on. &#8211;  [Aug 30 at 13:30]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1755804_1069945")
[*]First time is always tricky but it gets easier. Think that installing Windows in a pc with Ubuntu it would also be complex (probably more). There is tones of help and you are in the right place to find it. [askubuntu.com/questions/6328/how-do-i-install-ubuntu]("https://askubuntu.com/questions/6328/how-do-i-install-ubuntu") by the way, you can choose your partition and have Ubuntu take care of the rest. Just make sure you format it ext4 and mount it '/'. You will get used to the terminology in no time. Good luck! &#8211;  [Aug 30 at 15:51]("https://askubuntu.com/questions/1069945/lost-windows-after-installing-ubuntu#comment1755915_1069945")

[*]When I tried doing as you suggested, I get the following error "The ext4 file system creation in partition #5 of SCSI5 (0,0,0) (sda) failed."

[/LIST]

---

### Post by wildmanne39 on 2018-09-07
Hello and welcome to the forum!

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by lordfrikk on 2018-09-07
How exactly did you re-partition the drive to make space for your new Ubuntu installation?

---

### Post by lmangiac90 on 2018-09-09
I used the tools within windows 7 to chunk out ~100gb out of the 500gb drive (which at the time had about 200gb/500gb free, or ~300 gb occupied). I then turned the ~100gb partition into free space. Once I was on the ubuntu installation page, I reformatted it to ext4 and "/".

---

### Post by lmangiac90 on 2018-09-13
bump

---

### Post by HermanAB on 2018-09-13
The first thing to do is to backup your data.  After that you can do whatever you want.

At this point, the easiest way to backup your data is by booting with a live install CD and copy the data from the Windows partition to a USB memory stick.

The longer you wait to do that and the more desperate things your try, the more likely you will end up with no data.

---

### Post by oldfred on 2018-09-13
You are showing SFS for your Windows NTFS partitions. That is the way Linux shows Windows dynamic partitions.

It used to be that Linux would not see nor install with SFS on any drive. Now it seems to see it enough to let you install into unallocated space. But grub will not boot Windows in dynamic partitions and Windows will not boot Ubuntu.

You need to remove the dynamic partitions. Microsoft has no way, but some third party tools have worked for most users. Still have full backup.

 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by lmangiac90 on 2018-09-14
RE: back up

I've already done this, but thanks for the heads up!

---

### Post by lmangiac90 on 2018-09-14
> **oldfred said:**
> You are showing SFS for your Windows NTFS partitions. That is the way Linux shows Windows dynamic partitions.

It used to be that Linux would not see nor install with SFS on any drive. Now it seems to see it enough to let you install into unallocated space. But grub will not boot Windows in dynamic partitions and Windows will not boot Ubuntu.

You need to remove the dynamic partitions. Microsoft has no way, but some third party tools have worked for most users. Still have full backup.

 [http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758](http://ubuntuforums.org/showthread.php?t=2325331&p=13492758&viewfull=1#post13492758)
Microsoft's official policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas/Symantec for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Shown as SFS, Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx](http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx)
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
From Linux view LDM
[http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from](http://mika.soup.io/post/304505086/ldmtool-accessing-Microsoft-Windows-dynamic-disks-from)
[https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](https://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   [http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv](http://askubuntu.com/questions/482768/changing-windows-dynamic-disk-partition-to-basic-partition-and-not-the-full-driv) 
   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

Doesn't seem like I can go from dynamic disk to basic partition within linux, correct?

---

### Post by oldfred on 2018-09-14
I have seen some use testdisk when there are fewer than the 4 primary partitions.
But general rules are use Windows tools for Windows & Linux tools for Linux.

I also have these in my notes, but normally only post the Windows tools links.
       Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
[http://support.microsoft.com/kb/309044](http://support.microsoft.com/kb/309044)
Also used testdisk if less than 4 dynamic partitions
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)

---

