---
title: "[SOLVED] XP Partition Issue"
date: 2008-06-14
forum: General Help
---

### Post by riboch on 2008-06-14
I am having a serious issue.  

I recently installed Ubuntu on my laptop and had a horrible issue, I cannot get the XP partition to load, let alone mount.  I tried using the fixmbr and fixboot command on the windows disk and believe this is cause of all my troubles.  I would really like to recover the data on the XP partition if only to transfer it to another computer and reload this laptop.  I doubt it will matter, but I have an HP dv6604nr.  Below are the files and outputs I have seen the most on other posts.

When I use sudo fdisk -l, I get the following response:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e86f523

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2       19457   156280320    f  W95 Ext'd (LBA)
/dev/sda5               2       18357   147444538+   7  HPFS/NTFS
/dev/sda6           19397       19457      489951   82  Linux swap / Solaris
/dev/sda7           18358       19396     8345736   83  Linux

Partition table entries are not in disk order

/dev/sda5 is my XP partition. 

My fstab looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=574292d0-8274-4101-b51a-760a75f04983 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6074C91974C8F2B8 /windows        ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=67030245-6946-4996-8461-e843a8d520f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

My menu.lst has the:
### END DEBIAN AUTOMAGIC KERNELS LIST

title		Other Operating Systems:
root

title		XP Pro
root		(hd0,4)
savedefault
makeactive
chainloader 	+1


Thanks in advance.

---

### Post by JC Cheloven on 2008-06-14
So you have windows in a logical partition?  There's a lot of time I don't use windows, but as far as I remember, it needs a primary partition. 

Anyway, I'm not sure what you want exactly: boot from windows (as suggested by your use of fixmbr) or simply mount the partition from linux?

---

### Post by Rocket2DMn on 2008-06-14
Can you also please post
```
sudo blkid
```
Also, make sure that your moint point exists
```
sudo mkdir /windows
```
Then open fstab for editing
```
gksudo gedit /etc/fstab
```
Change the entry from
```
UUID=6074C91974C8F2B8 /windows ntfs defaults,umask=007,gid=46 0 1
```
to
```
UUID=6074C91974C8F2B8 /windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close, then run
```
sudo mount -a
```
Post the output of that command here as well.

---

### Post by Victormd on 2008-06-14
Since your NTFS partition is showing under fdisk -l, then take a look at the link on my signature to automount NTFS partitions.

Now, I'm guessing that you installed ubuntu after windows, in that case, you should be able to boot windows from the GRUB menu. If that's not the case, you can use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to fix your boot menu and include windows.

---

### Post by meierfra. on 2008-06-14
Since Xp is on a logical partition,  you must have deleted the partition containing the booting information for XP.  

(Or did you move XP from a primary partition to a logical partition? In this case you might be able to boot XP by deleting the "makeactive" from the  XP  item in menu.lst)  

If you would like,  I can show you how to boot XP in your circumstances. 
The procedure is outlined here:
[URL="http://ubuntuforums.org/showthread.php?t=813628"]
http://ubuntuforums.org/showthread.php?t=813628[/URL]
(Step 4 probably won't be necessary since you run "fixboot") 

Just  asked and I  write up detailed instruction for you.

Of course, this can  only work if  your XP Partition is intact. So first follow  the other advice is this thread and see whether you can mount the XP partition.

---

### Post by meierfra. on 2008-06-14
What happens when you try to mount XP by hand? Open a terminal and type

```
sudo mkdir Win
sudo mount -t ntfs-3g /dev/sda5 Win 
```

then try to browse the folder Win.
Report any error messages.

---

### Post by riboch on 2008-06-14
Before I begin this long post I would like to thank you for the responses and ask for your patience as I learn the ropes of this forum.

I believe the XP partition was changed from primary to logical, I am not familiar with how to fix this, so I will do a little research and get back to this.  I was originally using the AMD64 distro when I think I changed the partition type, but now I am using the non-AMD64 Ubuntu 8.04.  

> **JC Cheloven said:**
> Anyway, I'm not sure what you want exactly: boot from windows (as suggested by your use of fixmbr) or simply mount the partition from linux?

Currently, I would prefer to be able to dual boot, I still licensed program like MATLAB, Mathematica and UGS NX on XP that I would like to continue to use.  

> **Rocket2DMn said:**
> Can you also please post
sudo blkid[\Quote] 

sudo blkid produces:

/dev/sda5: UUID="6074C91974C8F2B8" TYPE="ntfs" 
/dev/sda6: TYPE="swap" UUID="67030245-6946-4996-8461-e843a8d520f0" 
/dev/sda7: UUID="574292d0-8274-4101-b51a-760a75f04983" TYPE="ext3"

I did have a /windows directory, and the subsequent commands produced no output, but did mount my cd/dvd drive.


[QUOTE=Victormd;5188092]
Now, I'm guessing that you installed ubuntu after windows, in that case, you should be able to boot windows from the GRUB menu. If that's not the case, you can use [SuperGRUB]("http://supergrub.forjamari.linex.org/?section=download") to fix your boot menu and include windows.[\QUOTE]

Yes indeed I did, on one of my desktops this was no issue, GRUB worked perfectly and included everything, but this was using the non-AMD distribution.  

[QUOTE=meierfra.;5188157][URL="http://ubuntuforums.org/showthread.php?t=813628"]
http://ubuntuforums.org/showthread.php?t=813628[/URL]

I will do this following my post.  I hope the partition is still intact.

No error messages were originally produced when I did this.  When I tried a second time I got
```
fuse: mount failed: Device or resource busy
```

I will get cracking at some of the links.  Thanks

---

### Post by Rocket2DMn on 2008-06-14
When you ran 
```
sudo mount -a
```
it didn't give any output?  That is good, that means the partition should be mounted at /windows - have a look there and see if the files on it are available.  Are they still not?

---

### Post by riboch on 2008-06-14
Yes, I can access them in the /windows.  I originally overlooked checking that.

Thanks.

---

### Post by meierfra. on 2008-06-14
> I believe the XP partition was changed from primary to logical, 

In this case  you should still have the  boot files. So just change your windows item in menu.lst to

title XP Pro
root (hd0,4)
savedefault
chainloader +1


Maybe this is all you need to do. Give it a try

  
I would guess that "boot.ini" is already correct. (it needs to say "partition(1)")

---

### Post by meierfra. on 2008-06-14
> Yes, I can access them in the /windows.

Good. Then look in /windows and see whether you have 
"boot.ini" , "NTLDR" and "ntdetect.com".  

If you do, open boot.ini  and see whether its says "partition(1)"

---

### Post by riboch on 2008-06-14
Pardon my excitement, but this is the most progress I have made in the past two days.  I made it slightly further on booting XP, I now get a "Disk Read Error."  Oddly I cannot find my boot.ini file in C:/.

---

### Post by meierfra. on 2008-06-14
> Oddly I cannot find my boot.ini file in C:/.

O.K. Then follow  the instructions from the link I posted earlier.  

Step 1) you already did (mounting the windows partition)

Step 2)  should be fairly easy

Step 3)  Skip this step. (Since the file "boot.ini" is already correct for you)

Step 4)  Skip this one, too.   It might already work without this Step.

---

### Post by Victormd on 2008-06-14
> **riboch said:**
> 
Currently, I would prefer to be able to dual boot, I still licensed program like MATLAB, Mathematica and UGS NX on XP that I would like to continue to use.

A bit off topic but have you heard of [Octave]("http://www.gnu.org/software/octave/")? It's an open source alternative to Matlab. :)

---

### Post by riboch on 2008-06-14
> **meierfra. said:**
> 
Step 2)  should be fairly easy


I will look more at this tomorrow with a fresh mind, my first attempt failed.  I am sure that if this is not the answer then it is in the right direction, so I will not place solved and begin my thanks yet.

> **Victormd said:**
> A bit off topic but have you heard of [Octave]("http://www.gnu.org/software/octave/")? It's an open source alternative to Matlab. :)

Yes, Octave and SciLab are just a couple of many reasons I am beginning the switch to Linux before grad school.

---

### Post by Victormd on 2008-06-15
> **riboch said:**
> Yes, Octave and SciLab are just a couple of many reasons I am beginning the switch to Linux before grad school.

I use MathCAD mainly but have used Matlab and later, octave, very nice... Still haven't found anything like Mathcad though which is the only reason I still use windows...

---

### Post by meierfra. on 2008-06-15
Detailed Instructions for Step 2)

Download this file:  [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573](http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573)

and save it to your Desktop. An icon with the name "Archive.tar.gz" will appear on your Desktop. 

RightClick it and choose "Extract here".

You should now have the folder "Archive" on desktop.

Open a terminal and type:

```
sudo cp Desktop/Archive/* /windows
``` 

Just to double check:

```
ls /windows
```

This lists all the files in the folder  /windows. Make sure that you now have "boot.ini", "NTLDR" and "NTDETECT.COM"


That's it. Just reboot and see whether you can get into  XP. 
( You can deleted "Archive" and "Archive.tar.gz"  at any time, but I would wait until you successfully booted into XP)

---

### Post by meierfra. on 2008-06-15
Just in case you were not able to  boot into Windows after you completed Step 2, here are the details for Step 4 (remember, Step 3 is unnecessary  for you)

Install and run "testdisk" via 

```
sudo apt-get install testdisk

sudo testdisk /dev/sda
```

Press "enter" to "proceed"
Press  "enter" to select "intel"
Use the "down arrow"  and "enter" to select "advanced"
Use the down error to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done just follow the instruction on the screen to save the new boot sector and quit testdisk.

That's it. Reboot and hope for the best.

---

### Post by riboch on 2008-06-15
Testdisk returned that the boot sectors were the same.  I then restarted and recieved the following error:

Windows could not start because of a computer disk hardware configuration problem.
Could not read from selected boot disk.  Check boot path and disk hardware.

I am very surprised by this, because even after moving my ntldr from /windows/WINDOWS to /windows and vice-versa, I did not recieve the "Cannot find the NTLDR" error.  I have tried using both NTLDR in the package and ntldr that was still in /windows/WINDOWS.  

I tried playing the partition(x) for both parts of the boot.ini, but to no luck.

I know this may sound strange, but I am just excited to see different errors, thank you.

> **Victormd said:**
> I use MathCAD mainly but have used Matlab and later, octave, very nice... Still haven't found anything like Mathcad though which is the only reason I still use windows...

I do not know too many people that use MathCAD, I think the only people here who are exposed to it are people who take the first two basic calc courses or came from other universities. 

I was exposed to MATLAB in my first and only programming course and have had so much success with it, and MATLAB tied with Latex, just amazing.  The only issue though is the cost of running it legally, and given the cost of toolboxes, simulink and the licenses, I do not know if my PI will support my wanting a personal copy.

---

### Post by riboch on 2008-06-15
I read too deeply into the instructions and set partition(1) to partition(5), as I understood it to mean the partition XP was on, oh well, it works fantastically. 

Next question, how to I add the solved tag to this and what is the etiquette on "Thanks," do I thank every poster, do I thank every post by every poster or every post by the poster who solved my issue?

Again, I apologize for my ignorance, but this is the first time I have ever used a forum.

What are some appropriate tags: Partition, Windows, Primary Partition, Logical Partition?

Thank you to all who helped.

Quick opinion, now knowing this procedure, do think it smart or safe to revert back to the AMD64 distro?

---

### Post by JC Cheloven on 2008-06-15
Hi riboch, congratulations.
Don't thank me, as I didn't anything for you really. I wasn't skillful enough with windows to do that. Thank the people that actually helped you ;-)

To thank one post from each person who helped you, would be enough.
I see that you found already how to mark "solved" under "thread tools"

---

### Post by linfidel on 2008-06-15
By the way, if you only use a few Windows programs, you may be able to create a Virtual Machine using Virtual Box, a free linux program that works well.  You would install XP in this, then install the programs.  It would save needing to reboot back and forth, although the graphics performance is slow in a virtual machine.

---

### Post by logos34 on 2008-06-15
> **riboch said:**
> I read too deeply into the instructions and set partition(1) to partition(5), as I understood it to mean the partition XP was on, oh well, it works fantastically.

That's what I had to set mine to also back when I was dual-booting with windows on a logical.

---

### Post by meierfra. on 2008-06-15
> I read too deeply into the instructions and set partition(1) to partition(5),

Just for the benefits of others looking at this thread: Let me explain why it has to be "partition(1)"

Your partition table looks like this:

sda1  : extended
sda2  : empty
sda3  : empty
sda4  : empty
sda5  : XP
sda6  : Swap
sda7  :Ubuntu

The instruction say:  Windows counts in order of the partition table, but it skips over extended partitions and empty partitions.

So in your case  sda1,sda2,sda3 and sda4 do not count.  This makes XP the first partition.


Lets do  another example. My partition table:

sda1:  Grub
sda2:  Suse
sda3:  extended
sda4:  empty
sda5:  Data
sda6:  Swap
sda7:  More Data
sda8:  Hardy
sda9:  XP


This time sda3 and sda4 do not count. So I have to use partition(7) in "boot.ini"

---

### Post by logos34 on 2008-06-15
> **riboch said:**
> I tried playing the partition(x) for both parts of the boot.ini, but to no luck.

Oh, so you changed it to point to sda5, but it didn't work either?

I thought when you said you "set partition(1) to partition(5)...oh well, it works fantastically", you meant '(5)' worked. 

But why then did the original 'partition (1)' not work in the first place? I'm still not clear on what exactly fixed the problem. 

I've always referred to [this guide]("http://www.goodells.net/multiboot/editbini.htm") in the past.

---

### Post by meierfra. on 2008-06-15
I'm pretty sure that the OP changed the "1" to "5" without ever trying "1". (at least that's  how I understood it)

Only after the OP set it back to "1", he/she was able to boot into XP.

---

### Post by riboch on 2008-06-16
My apologies, I had originally set partition(1) to partition(5) when it should have just been partition(1) to work, I started without ever trying partition(1), but this currently works as explained why above. 

Thanks to meierfra for explaining everything.

---

