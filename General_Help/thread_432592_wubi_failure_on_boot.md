---
title: "wubi failure on boot"
date: 2007-05-04
forum: General Help
---

### Post by sc00ter on 2007-05-04
Can anyone help?

Downloaded the latest build of the Wubi installer (minefind2), ran the installer which installed the alternative ISO to my D: (which was the partition with the lagest amount of free space).

Rebooted Windows XP when requested.

Selected "Ubuntu" when the windows boot menu appeared,  then it gets stuck on the screen:

[B]Booting 'Ubuntu'

find --set-root /wubi/linux

[/B]

I've left the system for upto 15 minutes with no disk activity, nothing. I've rebooted several times, but with the same results.

I've also uninstalled and removed the downloaded ISO and tried to install from scratch, but I'm afraid no joy - still the same results.

Any ideas?

---

### Post by sc00ter on 2007-05-04
After further reading of various posts, I moved the **wubi** folder from my D: partition to my C: and tried booting into Ubuntu again.

This time, it worked. I can now successfully boot into both Ubuntu and Windows XP.

Strange how I didn't get the **error 17** that has been reported in other posts.

For the record, my C: partition is installed on a primary (IDE) drive and the D: partition is on a secondary (IDE) drive.

---

### Post by ecology2007 on 2007-05-04
Good. Do you know if the faulty drive is fragmented or compressed ?

---

### Post by sc00ter on 2007-05-04
Definitely not compressed and unlikely it could be a fragementation issue, as Diskeeper is configured to defrag both C: and D: drives periodically.

I forgot to mention in my original post that I had forced a manual defrag prior to installation.

---

### Post by ecology2007 on 2007-05-04
You are right, if you do not see error 17 it is unlikely a fragmentation issue.
I have just made a post about that.
[http://ubuntuforums.org/showpost.php?p=2593543&postcount=5](http://ubuntuforums.org/showpost.php?p=2593543&postcount=5)

Do you know if D: is ntfs or FAT32 ? If it is connected through IDE or SATA ?
If D: is a SATA drive the new minefield could solve the issue :
[http://ubuntuforums.org/showthread.php?t=432808](http://ubuntuforums.org/showthread.php?t=432808)

---

### Post by chuyito_18 on 2007-05-05
Yes .. this is the solution to your problem .. when you install the wubi .. and the installer ask to reboot .. DON'T select the ubuntu option... select the Windows XP ... and then .. reboot it manualy and now you can select the Ubuntu option ..to complete the installation...

This is what i do .. and its workin fine now ... 

byes...

Jesus Soto



> **sc00ter said:**
> Can anyone help?

Downloaded the latest build of the Wubi installer (minefind2), ran the installer which installed the alternative ISO to my D: (which was the partition with the lagest amount of free space).

Rebooted Windows XP when requested.

Selected "Ubuntu" when the windows boot menu appeared,  then it gets stuck on the screen:

[B]Booting 'Ubuntu'

find --set-root /wubi/linux

[/B]

I've left the system for upto 15 minutes with no disk activity, nothing. I've rebooted several times, but with the same results.

I've also uninstalled and removed the downloaded ISO and tried to install from scratch, but I'm afraid no joy - still the same results.

Any ideas?

---

### Post by sc00ter on 2007-05-07
Both C: and D: are NTFS (uncompressed) and are IDE drives.

---

### Post by elibaba on 2007-05-09
Hi, this is my first post in this forum, so I'll hitchhike this thread as I have a very similar issue I am trying to solve.

I have a dell D610 laptop with 80GB XP disk, all in one partition. see image :

[IMG]http://forums.ort.org.il/files/30/2427852/4081082.JPG[/IMG]
(I have no idea what is the 94MB partition...)

Installed latest WUBI, defraged the whole drive, booted and I'm getting error 17 and the obnoxious  
"find --set-root /wubi/boot/grub/menu.lst"

I did not change any of the defaults, wubi is in C:\wubi, my boot.ini is :

```
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
grldr="Ubuntu"
```

I tried modifing the last line to ```
multi(0)disk(0)rdisk(0)partition(2)\grldr="Ubuntu" 
```but it won't boot this way.

grldr is in the root folder, as well as menu.lst wherer the significant lines are :
```
title Ubuntu
find --set-root /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst
```


I've exhausted all I know about booting :) , so can anyone please help ?

Thanks in advance!
C:\wubi\boot\grub\menu.lst exists and there there's:
```
title Ubuntu (Original Kernel)
find --set-root /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot
```

---

### Post by ago on 2007-05-09
Try to replace

find --set-root ....

with

root (hd0,1)



The first line finds the root that contains the specified file, the second command sets the target to first harddisk, second partion. Other way to debug is to comment out #hidemenu, increase timeout to 10. This will allow you to see the grub menu. Once you are at the grub menu hit "c". This will bring you to command line. Then type "root (hd" and hit tab. Tab will autocomplete and give you all possible options. You can also try to type "find filename"... help for a list of commands. If you understand why it did not work, let us know.

---

### Post by elibaba on 2007-05-09
Thanks for the reply, but I'm sorry to say it did not help much.

I have used contig to make sure the folder isn't fragmented :

```
C:\stuff>Contig.exe -s -v  c:\wubi\boot\*

Contig v1.54 - Makes files contiguous
Copyright (C) 1998-2007 Mark Russinovich
Sysinternals - www.sysinternals.com

------------------------
Processing c:\wubi\boot\grub:
Scanning file...
c:\wubi\boot\grub is already in 1 fragment.
------------------------
Processing c:\wubi\boot\initrd:
Scanning file...
Scanning disk...
File is 1909 physical clusters in length.
File is in 90 fragments.

Found a free disk block at 12708509 of length 1910 for entire file.
Moving 1909 clusters at file offset cluster 0 to disk cluster 12708509
File size: 7816818 bytes
Fragments before: 90
Fragments after : 1
------------------------
Processing c:\wubi\boot\linux:
Scanning file...
Scanning disk...
File is 427 physical clusters in length.
File is in 24 fragments.

Found a free disk block at 8752931 of length 428 for entire file.
Moving 427 clusters at file offset cluster 0 to disk cluster 8752931
File size: 1745100 bytes
Fragments before: 24
Fragments after : 1
------------------------
Processing c:\wubi\boot\winboot:
Scanning file...
c:\wubi\boot\winboot is already in 1 fragment.
------------------------
Processing c:\wubi\boot\grub\bzr_log.xLZJ4z~:
Scanning file...
c:\wubi\boot\grub\bzr_log.xLZJ4z~ is already in 1 fragment.
------------------------
Processing c:\wubi\boot\grub\menu.lst:
Scanning file...
c:\wubi\boot\grub\menu.lst is already in 1 fragment.
------------------------
Processing c:\wubi\boot\winboot\grldr:
Scanning file...
Scanning disk...
File is 41 physical clusters in length.
File is in 3 fragments.

Found a free disk block at 18514561 of length 42 for entire file.
Moving 41 clusters at file offset cluster 0 to disk cluster 18514561
File size: 167328 bytes
Fragments before: 3
Fragments after : 1
------------------------
Processing c:\wubi\boot\winboot\grub.exe:
Scanning file...
Scanning disk...
File is 44 physical clusters in length.
File is in 4 fragments.

Found a free disk block at 18544426 of length 45 for entire file.
Moving 44 clusters at file offset cluster 0 to disk cluster 18544426
File size: 178592 bytes
Fragments before: 4
Fragments after : 1
------------------------
Processing c:\wubi\boot\winboot\menu.lst:
Scanning file...
c:\wubi\boot\winboot\menu.lst is already in 1 fragment.
------------------------
Summary:
     Number of files processed   : 9
     Number of files defragmented: 4
     Average fragmentation before: 14 frags/file
     Average fragmentation after : 1 frags/file


C:\stuff>
```

Then, upon boot I entered the GRUB command editor and tried replacing 
find --set-root /wubi/boot/grub/menu.lst
with
root(hd0,1).. as you recommended, and there's something weird : the autocompletion of the path with TAB works only up to /wubi/boot/!
it does not "see" folders or files beyond this point, while in "/" I see my entire XP disk.

I think this is the reason why it can't find /wubi/boot/grub/menu.lst, from GRUB perspective there's nothing beyond /wubi/boot/ - the question is why ?

---

### Post by ago on 2007-05-09
are the files in there compressed (compression may be enabled at filesystem level)?

---

### Post by elibaba on 2007-05-09
No, they're not, that was my other guess but I'm stomped - I have no idea why it won't find menu.lst

---

### Post by ago on 2007-05-09
try with the kernel command

kernel (hd0,1)/wubi/ + hit tab key

see if you can set the kernel path (/wubi/boot/linux)

---

### Post by elibaba on 2007-05-09
/wubi + TAB gives /wubi/boot but not ufrther , as if it's the end of the folder structure

---

### Post by ago on 2007-05-09
Do you actually have files in there (visible from windows)?

---

### Post by elibaba on 2007-05-09
Of course :)  I am not that clueless...

[IMG]http://forums.ort.org.il/files/30/2428891/6791959.JPG[/IMG]

[IMG]http://forums.ort.org.il/files/30/2428892/5897672.JPG[/IMG]

---

### Post by cvcuse on 2007-05-09
Hi, Not able to 'arrow down' to highlight ubuntu.......time runs down, xp boots.
Thanks

---

### Post by ago on 2007-05-09
No real explanation on top of my head since I cannot reproduce the same error and my knowledge of grldr is limited (it's an external project). But see 

[http://ubuntuforums.org/showthread.php?t=438037](http://ubuntuforums.org/showthread.php?t=438037)
[https://bugs.launchpad.net/wubi/+bug/113641](https://bugs.launchpad.net/wubi/+bug/113641)

---

### Post by ago on 2007-05-09
> **cvcuse said:**
> Hi, Not able to 'arrow down' to highlight ubuntu.......time runs down, xp boots.
Thanks

Never seen that before, but that is unlikely to be an issue due to wubi/grldr. That menu is managed by windows (ntldr). Try to use control_panel > system > advanced > startup_and_recovery to edit/modify the windows menu and see if that fixes.

---

### Post by cvcuse on 2007-05-09
got me over here.......thanks
actually chose ubuntu when ask  'boot with xp' or ubu, clicked ok..............
got cold feet as thinking how will get back to 'xp' if not able to access windows/ control panel......
anyway reset 'xp' .ok.............thought  will check into accessing 'control panel ' once on the other side..............on the other side,now.........same situation ubu on top, xp below on boot , can't arrow down to xp to go back..................any help would be appreciated.........like what i see,just would like to go back to xp with no problems...................................

---

### Post by ago on 2007-05-09
As mentioned, I think that the issue is with ntldr, not much we can do. Anyway once in Ubuntu open up your C drive (usually you find it under /media/host/) and edit boot.ini changing the default boot option.

---

### Post by cvcuse on 2007-05-09
boot loader]

timeout=15

default=c:\grldr

[operating systems]

c:\grldr="Microsoft Windows XP Home Edition"

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect



above is what shows after inserting    'Microsoft Windows XP Home Edition'    line 5, it had"ubuntu"
went to restart............this time where 'ubuntu' was on top and "xp' below  boot screen ........both "xp"
thought well this time xp for sure .................didn't happen
any advice?

---

### Post by ago on 2007-05-09
The relevant line is 

default=c:\grldr

That decides what is booted by default. If you want to start windows set it to:

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

As for

c:\grldr="Microsoft Windows XP Home Edition"

that should read 

c:\grldr="Ubuntu"

Even though that only affects the menu title, functionality is the same.

---

### Post by cvcuse on 2007-05-09
> got to boot screen
ubuntu on top....win xp default .........highlighted
 time ran down...again not able to arrow up/down
 thought ok as highlighted............xp will boot



not................

message shown        <windows root>\system 32\ ha.l.dll.


what now?


Get sure you have a file named grldr and menu.lst next to boot.ini in your c: drive.
Else get grldr it from here, copy the menu.lst from the wubi folder to the c:

[http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip](http://download.gna.org/grub4dos/grub4dos-0.4.3-2007-05-09.zip)

---

### Post by elibaba on 2007-05-10
Hi, I managed to get some progress in running Ubuntu with Wubi:

1) I got the grldr from the link Ago gave earlier in this thread (10x!) and replaced my previous c:\grldr from wubi setup.
2) Tried to boot but still got error 17.
3) I moved "initrd", "linux", the iso file and all the rest from c:\wubi\boot\grub and c:\wubi\boot  to my root folder .

[IMG]http://forums.ort.org.il/files/30/2429143/9806882.jpg[/IMG]

4) I modified menu.lst in the root folder to point to these files :

```

#### MENU ITEMS BELOW HERE ####

title Ubuntu

find --set-root /linux
kernel /linux find=/linux setup_iso=ubuntu-7.04-alternate-i386.iso ro
initrd /initrd
boot
```

5) removed the "splash" and "quiet" directives to I'll be able to see what's going on.

The good news are that I'm booting the kernal now from the ISO, bad news are I'm getting

```
Begin: waiting for root file system...
```

And the boot sequence is stuck.


I think this is because virtual disks are still in C:\wubi\disks (home.virtual.disk, swap.virtual.disk, system.virtual.disk) and the kernel can't "find" them.

Any Ideas where should I put these files to be able to startup Ubuntu ?

---

### Post by ago on 2007-05-10
> **elibaba said:**
> 
I think this is because virtual disks are still in C:\wubi\disks (home.virtual.disk, swap.virtual.disk, system.virtual.disk) and the kernel can't "find" them.

Any Ideas where should I put these files to be able to startup Ubuntu ?

You need to keep the relative path from linux (kernel) the the wubi virtual disks and from linux to boot/grub/menu.lst


so from the folder conatining the kernel, the virtual disks are in ../disks and menu.lst is in ./grub/menu.lst

At the moment we are trying to understand why some files/folders become invisible to grldr. I cannot reproduce the error on my machine(s) so I cannot be of much help, but Ecology has the same error. If you can figure it out it might help.

It might be that the files are not contiguous: [http://ubuntuforums.org/showpost.php?p=2625960&postcount=16](http://ubuntuforums.org/showpost.php?p=2625960&postcount=16)

---

### Post by elibaba on 2007-05-10
Happy to post this reply from Ubuntu! \\:D/ 

I moved linux and initrd to c:\  (root folder)
In the root folder I have menu.lst that has :

```


find --set-root /linux
kernel /linux find=/linux setup_iso=ubuntu-7.04-alternate-i386.iso  ro
initrd /initrd
boot
```

"disks" and "install" folders where moved to c:\ too. "Install" has the iso image in it.

Basically I didn't leave anything meaningfull in c:\wubi, and now I can boot into Ubuntu!

Thanks a lot for your help!

---

### Post by tinybit on 2007-05-11
> there's something weird : the autocompletion of the path with TAB works only up to /wubi/boot/!
> it does not "see" folders or files beyond this point, while in "/" I see my entire XP disk.

The NTFS filesystem driver of grub4dos is probably buggy. If you use grub4dos with NTFS, you'd better place files in the root dir.

---

### Post by ago on 2007-05-11
> **tinybit said:**
> > there's something weird : the autocompletion of the path with TAB works only up to /wubi/boot/!
> it does not "see" folders or files beyond this point, while in "/" I see my entire XP disk.

The NTFS filesystem driver of grub4dos is probably buggy. If you use grub4dos with NTFS, you'd better place files in the root dir.

Straight into the root folder would be problematic, we can put everything inside /wubi and hope for the best. When that happened Ecology2007 mentioned that he could browse the rest of the filesystem fine, but not /wubi/boot. As mentioned the most annoying part so far is that we are not able to reproduce the error.

---

### Post by stubee on 2007-06-07
I'm having the same problem as the original poster (Sc00ter)

I chose to install to "D" drive, and I do see the virtual files under d:\wubi\disks
When PC is booting, and I choose "Ubuntu", it states:
Booting 'find/wubi/grub/menu.lst'
find --set -root --Ignore Floppies /wubi/boot/grub/menu.lst
==============
that's where it gets stuck...nothing else.  I have to hard boot.
==============

More Info:
- Originally attempted install via webpage (where it autodownloads iso), and forgot to change it to "d" on settings....so it installed to C
- Didn't work anyways...hung after listing drives.  (although I could ctrl-alt-delete). I wasn't concerned since I really wanted it on D.
- Uninstalled via windows add/remove
- Downloaded ISO, and Test3 to a sub directory on d:
- Ran Test3 install and it completes after a minute, and then tells me to reboot.  Choose ubuntu after reboot, and it gets stuck as described above.
- There is a GRLDR in both the root of C and D
================
Thanks for any info.

---

### Post by ago on 2007-06-07
Try [http://www.cutlersoftware.com/ubuntusetup/minefield.html](http://www.cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by stubee on 2007-06-07
Thanks for the quick response!

- I uninstalled Wubi (add/remove)
- Ran the file that you linked to, from the directory that contains the iso.
- It installed, and actually took an extra couple minutes to build the virtual files this time.  This version doesn't let you specify size of each folder....just the total.
- On reboot, choose Ubuntu

Booting GRLDR
Turning on Agate A20....Success
Starting Cmain()...

then nothing....had to hard boot.

---

### Post by Depressed Man on 2007-06-07
I'm getting similar problems as stubee when trying to install Ubuntu thru Wubi onto my desktop. I was trying to install on my F drive (C drive doesn't have enough space) though it did have remeants of grublr and all that stuff from a while back (does it need to be deleted?)

Even tried the suggested minefield and got the exact same error.

---

### Post by stubee on 2007-06-08
Ago:
Let me know if you want me to do any troubleshooting prior to your RC release.  I figure my prob may also affect some percentage of users.
Otherwise i'll just do the regular livecd install and see how that goes (ie partition resizing)

thanks.

---

### Post by ago on 2007-06-08
Yes that would help

1. Make sure the minefield is 179.52 or above
2. Make sure your boot folder is "clean": no menul.lst wubildr* grldr* grub*, no wubi/ubuntu in boot.ini, config.system or bcd
3. Do a fresh install

If it does not work tell me what files are installed under you boot folder, and run fstest.bat which should be in /wubi/tools

---

### Post by stubee on 2007-06-08
Maybe some progress here:
- Uninstalled wubi from add/remove
- noticed grldr was still present on the root of my D drive.  Removed it
- Installed via wubi-7.04-minefield-179.52.exe
- Rebooted, and selected Ubuntu

Now I get:
========================
(HD 0,0)  NTFS5: No GRLDR
(HD 0,1) Invalid or Null
(HD 0,2) Invalid or Null
(HD 0,3) Invalid or Null
(HD 1,0) Extended
(HD 1,1) Invalid or Null
(HD 1,2) Invalid or Null
(HD 1,3) Invalid or Null
(HD 1,4) NTFS5: No GRLDR
(FD 0):  Invalid or null
Error Cannot find GRLDR in all Devices (Ctrl-Alt-Del to reboot)
=======================
Indeed grldr is NOT in my Root C or D directory. (although there is a wubildr on both)

Additional Info:
- XP Pro OS
- Trying to install to D volume.

---

### Post by ago on 2007-06-08
There should be wubildr in c:\ and not grldr and boot.ini should be pointing to it

---

### Post by stubee on 2007-06-08
> **ago said:**
> There should be wubildr in c:\ and not grldr and boot.ini should be pointing to it

That is the way things stand after the install.  Maybe you misread my post?

---

### Post by Depressed Man on 2007-06-10
Getting the same thing as stubee. I also use Win XP Pro on my desktop and trying to install to my F drive.

---

### Post by ago on 2007-06-10
Please try the latest minefield it should fix the issue. 

1. Uninstall wubi
2. Check that there is no grldr/wubildr/menul.lst on your drive
3. Install Wubi 194.53

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by tinybit on 2007-06-10
> **stubee said:**
> 
Booting GRLDR
Turning on Agate A20....Success
Starting Cmain()...
then nothing....had to hard boot.

Just at boot time, press the INSERT key to single step the boot process. And post the result here please.

Or, press c instead of INSERT to forcibly enter command line. And at the grub console, type:

debug on
geometry (hd0)

Post the output please.

Also please post the content of your menu.lst file. If you did not intend to use any menu.lst file, you should delete them if they exist.

---

### Post by Depressed Man on 2007-06-10
> **ago said:**
> Please try the latest minefield it should fix the issue. 

1. Uninstall wubi
2. Check that there is no grldr/wubildr/menul.lst on your drive
3. Install Wubi 194.53

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

Goes back to this error

Booting 'find/wubi/grub/menu.lst'
find --set -root --Ignore Floppies /wubi/boot/grub/menu.lst

---

### Post by stubee on 2007-06-13
I gave up on getting Wubi install to work...and tried to just install from the Live CD.
Guess what...still an issue, so it appears my problem is not so much with Wubi but with Ubuntu (eventhough the LiveCD runs fine without installing)

I found what i think is the bug listed here:
[https://launchpad.net/~ubuntu-kernel-team/+assignedbugs](https://launchpad.net/~ubuntu-kernel-team/+assignedbugs)
Item: 107774

Basically something to do with how they changed the IDE interface in Ubuntu 7.04 and that pata_sis drivers don't work for those of us that have machines that require it.

---

### Post by Depressed Man on 2007-06-15
I also switched to using a live CD to install (was going rearrange my partitions anyway which included wiping Windows for a clean install of it anyway). Live CD option worked perfectly though.

---

