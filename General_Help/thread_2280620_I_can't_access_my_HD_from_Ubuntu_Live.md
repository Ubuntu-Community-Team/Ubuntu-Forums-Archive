---
title: "I can't access my HD from Ubuntu Live"
date: 2015-06-01
forum: General Help
---

### Post by sdas2 on 2015-06-01
Let me first say that I use Ubuntu only those rare times I have a problem with Windows, and trying to recover my files.

Premise: some days ago on Win I booted my PC and on Desktop an error showed up saying there were some errors in my HD and needed to reboot. If I recall right I had similar warning many months ago when a technician said he built a mirror RAID, but starting Win the first time I had the PC at home showed this warning and at reboot there was no RAID (can't say if there were a RAID on the first boot before the warning; also I don't want to get again in contact with that technician) but maybe all of this is irrelevant. And now after some months of use (plus Win updates and consequently restarts) I had this warning, rebooted and this time it started with [[ATTACH=CONFIG]262345[/ATTACH]]("http://ubuntuforums.org/asset.php?fid=258856&uid=1985907&d=1433155665") but about at 64% it restarted and it got on the same screen but directly  at 100%, but then the monitor went black and didn't see any activity  from the HD LED on my case. I tried some recover option from the  built-in Win8 recovery but without success; tried using a recovery point but there were none; in prompt I used 'sfc /scannow' and it was over in about 60 seconds (in a  2TB HD half full!), it found something and recovered it and restarted but  again it went with a black screen; tried 'chkdsk /r C:' over in 2  seconds and found no error but I read 358399KB of total space on disk!  (also isn't weird that in promp I have "X:\" instead of "C:\"?)

Now I'm on Ubuntu Live and would like to see if I can retrieve my files, but don't know how to access my HD (2x2TB not in RAID, one of them with Wind, and the other isn't touched from quite long because It have some bad sectors and now it's like an outdated backup drive).
I have this: [ATTACH=CONFIG]262346[/ATTACH], [ATTACH=CONFIG]262347[/ATTACH], [ATTACH=CONFIG]262348[/ATTACH], [ATTACH=CONFIG]262349[/ATTACH], [http://imgur.com/a/CFUf4#0;](http://imgur.com/a/CFUf4#0;) but actually this is the third time I use Ubuntu Live (since this problem), and the second time I had this: [http://imgur.com/a/ma00Y](http://imgur.com/a/ma00Y). See the differences and the RAID reference? On this second time I tried opening the first 3 icon on the first image previously posted in [http://imgur.com/a/ma00Y](http://imgur.com/a/ma00Y), and I got: "Unable to mount location. Error mounting: mount exited with exit code 21: fuse: mount failed: Device or resource busy".
So I really don't know what should I do; if I can't recover Win at least I would like to retrieve my files, please help me and sorry for the long post.

---

### Post by yancek on 2015-06-01
> "Unable to mount location. Error mounting: mount exited with exit code 21: fuse: mount failed: Device or resource busy".

That message shows frequently when booting a Linux system and a windows system has not been properly shutdown.  The Linux system will not mount the windows system due to this because of a likelihood of damaging the windows system.  I don't know that you will be able to access windows from Linux without repairing the drive.

Do you recall the specific recovery option you used with windows 8?

Since the problem is specific to windows, you would probably have better luck at a windows forum.  On the other hand, many members here also use windows so you may get some response here

---

### Post by grahammechanical on 2015-06-01
Here are some programs for recovering data and even fixing disks. Some of these programs are Windows only. Others come in Windows, Mac and Linux versions.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You are going to need somewhere to recover the data to. Is that second hard disk usable? Windows has detected something wrong. And when we get notices like that we know the first thing we should do once the OS has loaded is to backup all data that we want to save.

You could try installing Windows on that second hard disk and take it from there.

Regards.

---

### Post by sdas2 on 2015-06-01
> **yancek said:**
> That message shows frequently when booting a  Linux system and a windows system has not been properly shutdown.  The  Linux system will not mount the windows system due to this because of a  likelihood of damaging the windows system.  I don't know that you will  be able to access windows from Linux without repairing the drive.

Do you recall the specific recovery option you used with windows 8?

Since the problem is specific to windows, you would probably have better  luck at a windows forum.  On the other hand, many members here also use  windows so you may get some response here
Even if Win is installed only on 1 of the 2 HD?!
On [http://images.anandtech.com/doci/4771/Build-4632.jpg](http://images.anandtech.com/doci/4771/Build-4632.jpg) the first said there were no restore point, Automatic Repair failed, and safe mode too.

> **grahammechanical said:**
> Here are some programs for recovering data and even fixing disks. Some of these programs are Windows only. Others come in Windows, Mac and Linux versions.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You are going to need somewhere to recover the data to. Is that second hard disk usable? Windows has detected something wrong. And when we get notices like that we know the first thing we should do once the OS has loaded is to backup all data that we want to save.

You could try installing Windows on that second hard disk and take it from there.

Regards.
I'll look the link.
Do you know how can I install Win on the "bad" HD without touching the primary?

Also how can I understand if there is a RAID right now?

---

### Post by yancek on 2015-06-01
> Even if Win is installed only on 1 of the 2 HD?!

If there are inconsistencies in the ntfs (windows) filesystem, it is not likely to mount the drive you want.  You indicated you thought the other drive was bad for some reason so that would present problems also.  To determine if you have raid from Linux, you can try the commands suggested at the post below.  Never used raid myself so...?

To install to a specific drive, you would need to determine which is which.  You can do that from a terminal in Linux with the command:  sudo fdisk -l(Lower Case Letter L in the command).  That will display information on your drives/partitions which you can post here.

---

### Post by sdas2 on 2015-06-02
> **yancek said:**
> If there are inconsistencies in the ntfs (windows) filesystem, it is not likely to mount the drive you want.  You indicated you thought the other drive was bad for some reason so that would present problems also.  To determine if you have raid from Linux, you can try the commands suggested at the post below.  Never used raid myself so...?

To install to a specific drive, you would need to determine which is which.  You can do that from a terminal in Linux with the command:  sudo fdisk -l(Lower Case Letter L in the command).  That will display information on your drives/partitions which you can post here.

[ATTACH=CONFIG]262361[/ATTACH], [ATTACH=CONFIG]262362[/ATTACH]
You can see here SMART of the "bad" HD, fdisk command, and TestDisk in progress (which I'm still learning to use).
Actually I really hoped for a magical sudo command which let me access my HD! :mad:

---

### Post by sdas2 on 2015-06-02
TestDisk is over and I get this: [ATTACH=CONFIG]262370[/ATTACH], [ATTACH=CONFIG]262371[/ATTACH]
This program is above my level of comprehension (I would like if possible an hand here!), and I fear that modify partitions the wrong way to recover Win will get me to lose my files, but somehow now I'm able to retrieve my files (maybe I first backup them and then see if I can recover even Win later)! So thanks for the program!
But another problem arose: I think I pressed ctrl+c and the program lost its interface, is there a way to retrieve it? [ATTACH=CONFIG]262375[/ATTACH]  Restarting the program takes more than 7 hours!
EDIT: I also made a mess with the attachments, you can ignore the bottom one as I can't delete it (I'm a power user, am I not?).

---

### Post by sdas2 on 2015-06-12
I finally made a full backup!
Now for the recovery part: I now remember the first weird warning was on Win7, then I did a clean install of Win8 so I can exclude a RAID made by Win, right? Also in the bios there isn't any RAID configured. Then how could a RAID be still possible (I don't have an HW RAID controller)?
Despite the backup, I still want to try to recover Win, therefore I want to be sure of what action I should now do! So I want to delete any possible leftover of a RAID.

I did this:
```

ubuntu@ubuntu:~$ cat /proc/mdstat 
Personalities :  
unused devices: <none>

```
is the result like this because my 2 HD aren't shown on Ubuntu (the situation in [http://i.imgur.com/u96Cfwo.png](http://i.imgur.com/u96Cfwo.png) has never appeared again) and I'm on a LiveCD?

---

### Post by sdas2 on 2015-06-15
Now I only want to do a clean install of Win, but if I don't first fix this error it could show up again.

I tried:
```
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/mapper/pdc_dibheheia 
no raid disks and with names: "/dev/mapper/pdc_dibheheia" 
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/sdb 
Do you really want to erase "pdc" ondisk metadata on /dev/sdb ? [y/n] :y 
ubuntu@ubuntu:~$ sudo dmraid -r -E /dev/sda 
Do you really want to erase "pdc" ondisk metadata on /dev/sda ? [y/n] :y
```
and now I have this [ATTACH=CONFIG]262608[/ATTACH], and on the bottom there is still [http://i.imgur.com/tb0AnRa.png](http://i.imgur.com/tb0AnRa.png) .
I then tried for the latter (I suppose this made the problem) "Format Drive" > "Don't partition" but I got "One or more block devices are holding /dev/mapper/pdc_dibheheia". There is still "Format Volume" but I don't know if use NTFS or Empty (if it will work anyway).
Any help?

---

### Post by sdas2 on 2015-06-20
I think I solved.
I just had to restart to apply "dmraid -r -E" changes. I did again this command and "no raid disks and with names:...". Then I did a clean install of Win8.1. As you can see in [ATTACH=CONFIG]262731[/ATTACH], [ATTACH=CONFIG]262730[/ATTACH], [ATTACH=CONFIG]262729[/ATTACH], [ATTACH=CONFIG]262728[/ATTACH], [ATTACH=CONFIG]262727[/ATTACH] there isn't anymore the 2TB on the bottom in Disk Utility. 
However I have some thoughts: 
- do you think it's alright from these screen? 
- why 4 volumes? 
- those "unknown" exist maybe because Disk Utility (v2.30.1) and GParted (v0.5.1) are older than the newer Win8 and miss some info? (I tried updating them but maybe my Ubuntu version (10.04) is too old to support a newer version?) 
- why it's written "Linux Partition"?! 
- I have the second HD which I must format to be able to use it; in Win from Disk Management there is (image from internet: [http://www.computerhope.com/jargon/g/gpt.jpg](http://www.computerhope.com/jargon/g/gpt.jpg)) GPT preselected, but will I be able to access files from Ubuntu again (just in case!) if I'll use this despite the shown note? 
 
Now that I remember there was a warning in Device Management in Win about a device missing drivers or something like in [http://www.otherdevices.org/wp-content/uploads/2012/12/device-manager-with-devices-with-missing-drivers.jpg](http://www.otherdevices.org/wp-content/uploads/2012/12/device-manager-with-devices-with-missing-drivers.jpg)...can I aks for curiosity how the PC didn't fail for all these months?! How this error existed in the first place? 
Also why now during boot I don't anymore have the Win logo but the motherboard one? If I'm not mistaken, from the previous time I installed Win, I changed in the bios the boot priority from CD to CD.UEFI, and now in the bios I see HD.EFI before HD in the priority; should I change something?

If someone doesn't have all the answers, please post anyway!

---

