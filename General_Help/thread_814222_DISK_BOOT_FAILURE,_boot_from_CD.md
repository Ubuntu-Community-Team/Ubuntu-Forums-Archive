---
title: "DISK BOOT FAILURE, boot from CD?"
date: 2008-05-31
forum: General Help
---

### Post by Yellowbelly on 2008-05-31
Apparently my computer doesn't want to cooperate anymore. It crashed earlier today, in windows no less, and every time I tried to reboot, it wouldn't load up the grub or boot menu because of who knows what. It said: Booting from CD: DISK BOOT FAILURE, load system cd and press enter. Of course there was no CD in the tray.

I thought it was strange since it's supposed to say Booting from GRUB or something of that sort. I went in the bios and changed the boot sequence and removed anything with CD in it so it was harddisk for 1 2 and 3. It still said booting from cd. I then proceded to use my Linux Ubuntu 8.04 live disc and it started just fine. Loaded up the other systems, Started the grub, selected windows and shazaam, I'm here writing this. I was freaking out because I thought my HD fried but apparently it's working ok. What kind of aliens took over my system? I did just finish hl2 ep 2. Do I need to update the bios? I have no idea what's going on. I don't even know if this is the right forum for this.

---

### Post by quelx on 2008-05-31
I think it is telling you there is a hard drive failure of some sort.

Load the Ubuntu Live CD and boot from it.

Open a terminal windows and ```
sudo fdisk -l
```
to see if Ubuntu can see your hard drive.

Post the output here and we will see what we can do.

---

### Post by Yellowbelly on 2008-06-06
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9d7b9d7b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10991099

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       15017   120624021    b  W95 FAT32

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x730cf221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12475   100205406    b  W95 FAT32
/dev/sdc2           12476       19332    55078852+  83  Linux
/dev/sdc3           19333       19457     1004062+  82  Linux swap / Solaris

---

### Post by Yellowbelly on 2008-06-06
I opened up ubuntu for the first time since this problem started occurring and that 40.0gb HD has a locked emblem on it and I looked in properties and apparently the permissions couldn't be determined or so it says. This harddrive has my windows os on it.

---

### Post by rraj.be on 2008-06-06
I think you'r problem is hard disk fail's to boot.

had you turned off your PC without proper shut down?

Try some fix like booting from windows cd and entering in repair mode.

Else get your live cd and run fsck.

if you could connect your hard drive in any other windows machine just run chkdsk from that.

these surface scan may give you an idea about the problem.

May i know if further any thing arises for you.

---

### Post by Yellowbelly on 2008-06-10
yeah, sometimes it does it if I don't properly shut down my computer but I have been. I think it seemed to do it right after windows checked the drive possibly.

How do I run fsck?

---

### Post by Herman on 2008-06-11
Try this link and see if it helps you, [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").

---

### Post by Yellowbelly on 2008-06-11
sweet, but why do I have to unmount the fs before hand? and I guess that just means to unmount the partition correct? Also, it doesn't fix ntfs does it?

---

### Post by Herman on 2008-06-11
> sweet, but why do I have to unmount the fs before hand?Running a file system check on a mounted file system is kind of like driving your car and trying to fix a flat tire while the wheel is still turning.
> and I guess that just means to unmount the partition correct?If you run your file system check from a live CD you won't have to unmount any file systems beforehand, as long as you don't mount them in the first place.
If you are working from another installed operating system in your hard disk, sometimes there's an entry in /etc/fstab to automatically mount all your file systems on each boot up. In that case you need to unmount the file system you want to run a file system check on.
The command for unmounting a file system is 'umount /dev/sda1' or something like that, (change the '/dev/sad1' part to whatever you need). There's no 'n' in 'umount'. Dont' ask me why, there just isn't. 
 > Also, it doesn't fix ntfs does it?     No, fsck isn't for NTFS, that's an alien file system type. However, if you install ntfsprogs, you can run a file system check in an NTFS partition from Ubuntu. 
If the file system contains a Windows operating system, I would recommend running CHKDSK /R from a Windows XP [Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") instead though.
You can do it from Ubuntu with ntfsfix, I have used it and it worked well for me when CHKDSK couldn't do it. Actually, I fixed an '[A Disk Read Error Occured]("file:///media/WEBSITE/hermanzone/p15.htm#A_Disk_Read_Error_Occured")' for a friend of mine by moving a Windows partition to the other end of a hard disk with Gnome Partition Editor in Ubuntu Hardy Heron Live CD. CHKDSK /R didn't work, no matter how many times I ran it, but I fixed it with Linux tools, including ntfsfix.
EDIT: I have since found out that ntfsfix doesn't actually do anything much, but marks the NTFS file systems as 'dirty', so that Windows will check it at boot time.
Anyway, here's a link for you about working on alien on those alien file systems, [NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance") - Windows CHDSK - Linux ntfsfix.

---

### Post by Yellowbelly on 2008-06-12
Weird. I ran partition editor from the live cd and it detected all my devices but it noticed that the windows partition had an error and needed to run chkdsk /f. is that any different than /r?

I've read that I can do it from cmd, not just the recovery console. What would be the difference?

---

### Post by Herman on 2008-06-12
Yes, *if you can boot Windows in the first place*, you can schedule run CHKDSK to run in Windows next time Windows is booting up, (just before the kernel mounts the file systems I imagine). How to do that from GUI is already explained in the link, here it is again, [NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance") - Windows CHDSK - Linux ntfsfix.
That's the most obvious way and I expect that might be the most popular with Windows users. 
Or, *if you can boot Windows in the first place*, you can schedule CHKDSK to run at the
next reboot as explained in this link,  [How to Run Microsoft CHKDSK from the command line]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004066687571562").- symantec. That explains how to do it from cmd. 
Essentially, there's no difference at all between this and the first method of scheduling a CHKDSK, just two different way to do exactly the same thing. This way is just slightly 'geekier'. :)

*If you are unable to boot Windows*, or even if you can, and just if you prefer this method, you can run CHKDSK from your 'Windows XP Installation Disc', this is the geekiest method of all. 
(Can be done just for fun to impresses any visitors you may have watching to see how cool you are). 
The following link is the best I have found yet for explaining all about how to use the [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").
You just boot with your XP CD in your CD/DVD drive and press any key to boot from CD, then select a number corresponding the the Windows drive letter you're wanting to work on, then type your administrator password if you have one, usually leave it blank and press enter, then type 'CHKDSK /R' after the prompt.

If you just run CHKDSK with no options, it just does a dry run and tells you if there are any errors, I don't know why anyone would want to waste their time doing that though. Maybe if they don't have their data backed up yet and they're scared, (which doesn't seem logical to me), but you can run CHKDSK without any switches if you want to, apparently.
The /f switch fixes errors, ( 'f' for 'fix', I guess).
The /r switch ('r' for 'recover'), not only fixes file system errors, but also looks for bad sectors' in the hard disk and recovers readable information. The /r switch probably takes longer, because it does more work.
A 'bad sector' in a hard disk is an area where the hard disk's magnetic properties are getting weak, and there's a risk that further deterioration of that spot on the hard disk might result in some data being lost. 
I prefer to run CHKDSK with the /R switch.

There are lots of spare sectors at the end of the hard disk that can be swapped for any bad sectors, (kind of like having lots of spare tires). When you run out of those, it's time to start shopping for a new hard disk. Most hard discs last about five or ten years, depending on the quality of their manufacture and how much you use them and lots of other things, (environmental factors).
All hard disks have bad sectors, even when they are brand new. As the hard disk ages, a few more crop up from time to time.
Heat from the hard disk's motor and bearings is one of the main reasons why hard disks deteriorate, so if your computer case has good air circulation around and in between your hard disks, your hard disks are likely to last longer.
It's important to keep a space between computer case vents and a wall, or other objects like books and things that might be on a computer desk.
It's also good idea to look behind a desktop PC and check the case vents every once in a while and make sure they're clear and not clogged up with dust.

---

### Post by Yellowbelly on 2008-06-13
I did the chkdisk thing by gui with both options checked and it didn't work. I tried through cmd but it had the same option of doing it at start up so it'll take the recovery console to do it but I doubt it would be any better. Should I try it through the live cd or ubuntu os?

---

### Post by cariboo on 2008-06-13
If you got another computer or you can get yours running well enough download a copy of Hiren's boot disk and use the hdd testing utility for your hard drive to test your drive. You'll have to do a search for Hiren's boot disk as it is not available through regular channels.:)

Jim

---

### Post by Herman on 2008-06-13
> I did the chkdisk thing by gui with both options checked and it didn't work. I tried through cmd but it had the same option of doing it at start up so it'll take the recovery console to do it but I doubt it would be any better. Should I try it through the live cd or ubuntu os?I would try to get ahold of a Windows XP 'Installation Disc' and use the  [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"). 

I agree with cariboo907, but I'm not so familiar with Hiren's Boot Disk. I use smartmontools in Ubuntu for that job, 
```
sudo apt-get install smartmontools
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo smartctl -s on /dev/sda
```[FONT=Bitstream Vera Sans Mono]
[/FONT]```
sudo smartctl -a /dev/sda >> harddiskreport
```
Look for a file named 'harddiskreport' in your /home/usernam directory and open it.
The Wikipedia has the best key for making some sense from the output,  [Self-Monitoring, Analysis, and Reporting Technology]("http://en.wikipedia.org/wiki/Self-Monitoring,_Analysis,_and_Reporting_Technology").

---

### Post by cariboo on 2008-06-13
here is a link to what is included in hiren's boot disk:

[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)

Jim

---

### Post by Yellowbelly on 2008-07-29
I think it's time to resurrect this thread because I've had more problems. This time it had some heavy use. Yesterday, I was cleaning out my computer because I have tons of files that are just sitting around and I really need to clean up some HD space on that windows hard drive sda I think it was. I was also trying to fix up some id3 tags on songs so I installed and uninstalled that program. Needless to say I probably put a lot of stress on it. The first weird thing I noticed was that FireFox wouldn't open. I used it all day but at the end, it wouldn't open for anything. There was some error with opera (module 7????) so I had to revert to IE to get anything done. I had to leave it running to finish some downloads. Anyway, I figured it just needed a heavy restart so this morning I do that. Tried to load up windows and I get the classes: windows did not startup/shutdown properly, load safe mode or normal. I click on normal, I just think safemode is a joke 99% of the time and windows is useless to me in safemode. Anyway it doesn't start (screen goes black, thinks about it, then the start up begins) so it automatically reboots the computer. I think it's dead. Is it time to get a new one? Ubuntu doesn't even recognize it anymore. The partition shortcut isn't even on my desktop.

thanks

---

### Post by Herman on 2008-07-29
> I think it's time to resurrect this thread because I've had more problems. This time it had some heavy use. Yesterday, I was cleaning out my computer because I have tons of files that are just sitting around and I really need to clean up some HD space on that windows hard drive sda I think it was. I was also trying to fix up some id3 tags on songs so I installed and uninstalled that program. Needless to say I probably put a lot of stress on it. The first weird thing I noticed was that FireFox wouldn't open. I used it all day but at the end, it wouldn't open for anything. There was some error with opera (module 7????) so I had to revert to IE to get anything done. I had to leave it running to finish some downloads.I have fixed Windows for freinds who use it a number of times now when it wouldn't even boot at all by running chkdsk /r trying to boot it in safe mode. As soon as I can get it to boot I run a disk cleanup and defragment the drive repeatedly and most often if there are no bad viruses, a sick Windows OS will become bootable again.
'Safe mode' means Windows can boot with a minimum number of drivers, so you can fix it enough to work properly in normal mode. 
> Anyway, I figured it just needed a heavy restart so this morning I do that. Tried to load up windows and I get the classes: windows did not startup/shutdown properly, load safe mode or normal. I click on normal, I just think safemode is a joke 99% of the time and windows is useless to me in safemode. Anyway it doesn't start (screen goes black, thinks about it, then the start up begins) so it automatically reboots the computer. I think it's dead. Is it time to get a new one? Ubuntu doesn't even recognize it anymore. The partition shortcut isn't even on my desktop.You shouldn't ever do a 'hard restart' if you can possibly avoid it, that's not very good for either your hard drive or for your file systems. 
You should always shut down your operating systems from the menus in the operating systems so that the operating system will shut down the computer, not by removing the power with the big 'Off button'. That doesn't give the operating system time to tidy up and put things away first.
You can probably still fix it with chkdsk /r.
If you have a little spare money, another hard disk is always nice though, they're not as expensive these days as they used to be. If your computer can accomodate another hard disk then it might be a good idea to have two hard disks in your computer. You can use the extra one for backups, or you can install Ubuntu in one hard disk and Windows in the other. :)

---

### Post by Yellowbelly on 2008-07-30
I meant restart as in doing it normally through menus, not a hard button restart.

well since I tried the chkdsk, I guess I could try the other ubuntu based ones but ubuntu doesn't even recognize that it exists anymore. I have 2 other harddrives so i'm not hurt, I just still have to use the boot disks and any chances of me playing a video game is nil which could only help productivity through boredom. Another possiblity is that could it be that a jumper or cable from the hd is coming loose?

---

### Post by Herman on 2008-07-30
> I meant restart as in doing it normally through menus, not a hard button restart. Oh, okay, sorry, I misunderstood.
> well since I tried the chkdsk, I guess I could try the other ubuntu based ones but ubuntu doesn't even recognize that it exists anymore. I have 2 other harddrives so i'm not hurt, I just still have to use the boot disks and any chances of me playing a video game is nil which could only help productivity through boredom. Another possiblity is that could it be that a jumper or cable from the hd is coming loose?
Check your cables and make sure they're plugged in securely. 
Other than that you should be able to run some tests to try to determine if the hard drive is really going bad. 
Try [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check").
```
sudo badblocks -sv /dev/sda1
```You can also see what's wrong with your hard disk sometimes if you install smartmontools, ```
sudo apt-get install smartmontools
```To get smartmontools to query the memory in your hard disk's firmware and print the output to a file named 'harddiskreport', you can use a command like this,
```
sudo smartctl -a /dev/sda >> harddiskreport
```Some of the information in the hard disk report should be intelligible to humans, but quite a bit of it is vague even to experts, but it should still give you some indication.
I am told that 'Hiren's Boot CD' contains vendor specific hard disk drive testing software, and that might be worth a try, smartmontools will tell you what make and model of hard disk you have and lots more to get you started.

Otherwise, if you have a little spare cash, maybe you should just go buy yourself another new hard disk. They're generally  a lot more affordable these days than they used to be, even just a year ago.
Or use one of your spare hard disks instead.
Usually the data you store on a hard disk is worth a lot more than the price of a new hard disk, so it's probably a good idea to replace the hard disk if you're in doubt.

---

### Post by Yellowbelly on 2008-08-10
I just got back from a trip and ran bad blocks. Here's what it says:
```

done                                
Pass completed, 36994 bad blocks found.


```
Is that bad?

---

### Post by Herman on 2008-08-11
> I just got back from a trip and ran bad blocks. Here's what it says:
 	Code:
 	done                                
Pass completed, 36994 bad blocks found. 
Is that bad?
:shock: Yes, I would say that is definitely bad.
If I were you I'd be backing up all the data I can and going shopping for new hard disk.
I think your hard disk is on it's way out.

Regards, Herman

---

### Post by Yellowbelly on 2008-08-11
hahaha. this actually kinda works out just fine. I have practically nothing on that drive because I put everything on a 90gb partition shared by my dual boot. I just backed up some photos.

Also, if I get a sata drive, will that work with the rest of my IDE's?

---

### Post by Herman on 2008-08-11
SATA drives will work fine with IDE drives, except you may find that someday when you perform a fresh Linux installation, there might be a little confusion between your BIOS and GRUB and Linux in deciding which is number 1 hard drive and which one will be number2 and so on. 
It can be a little confusing for the user at first with a fresh installation, but once you get your GRUB set up properly, there are no other problems with having IDE and SATA hard disks in the same computer.
My computer (the one I'm typing from right now) has two IDEs and two SATAs and it had no problems at all with Ubuntu Feisty, or Gutsy Gibbon's GRUBs. 
For some reason Hardy and Interpid's GRUBs seem to be the ones that needed their menu.lst files edited to make them boot up properly. I had to enter the 'wrong' hard disk number in their booting stanzas in menu.lst to get them to boot properly. (Sometimes two wrongs do make a right). :)

---

### Post by Yellowbelly on 2008-08-11
Yikes. It seems like they took a step back with hardy. It doesn't make much since. Anyway I have a pretty aged computer. Built 5 and half years ago with the most recent upgrade at at least 2-3 years. I might upgrade everything so would you suggest to move to SATA and just tinker with it if needed or go with IDE again?

---

### Post by Herman on 2008-08-11
I don't know, SATA drives are supposed to be faster, I think the speed of the information travelling to and from the hard drive is faster, from what I have read, but the same old hard disk platters and read and write heads still have to do the same work, and those still run at the same old speed, regardless if it's IDE or SATA. The information is stored in the hard drive's cache (memory) for a short time while the read and write heads catch up, so no matter if you get IDE or SATA, prefer a hard drive with a bigger cache memory if you are comparing two hard disks that are otherwise equal.
I don't notice much speed difference between my IDE disks and SATA disks, maybe I'm not paying enough attention. Maybe if I set a stopwatch and moved some very large files around I'd notice a difference. In regular use it's hard to tell, it doesn't seem to matter.

---

