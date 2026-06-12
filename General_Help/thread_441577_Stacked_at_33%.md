---
title: "Stacked at 33%"
date: 2007-05-12
forum: General Help
---

### Post by DominoBB on 2007-05-12
I am trying to install Ubuntu with the Wubi installer.
The windows part goes with no errors. The Ubuntu installation is being copied from the site and I am being asked if I want to reboot now or later. I reboot, I chose Ubuntu from the screen and then I wait. I get to the point were it says that the applications are being copied and after that it says that the virtual drive is being formatted and that this may take some time. The process bar goes almost immediately to 33% and then nothing. It stays at 33% without moving. I waited for about 15 minutes and it was still 33%.

Anyone know what could be the problem?

---

### Post by mazingersama on 2007-05-12
I had the same problem when I was installing wubi. I think that our problem is hard disk driver is not supported. My hard disk is TOSHIBA MK8007GAH.

---

### Post by DominoBB on 2007-05-12
I have a Maxtor hard drive.
So did you install Wubi eventualy?

---

### Post by Jerick on 2007-05-13
I'm not sure if it is the hard disk driver. I'm on a SATA Western Digital, and am getting the same issue.

---

### Post by spikyjoe on 2007-05-13
Same here.
I am trying to use a using a Sony Vaio VGN-S4M/S

---

### Post by ago on 2007-05-13
Wait a little bit, you can also press alt+f4 for more feedback. Also select smaller disk images of 4-5GB or so.

---

### Post by mazingersama on 2007-05-13
You were right, I changed size to 4 gb and It could be installed perfectly, thanks a lot.

---

### Post by ago on 2007-05-13
Can you try to start with a 3GB virtual drive and go up to see if there is a size that will jam the formatter? I will also create a special bulild later on with a change that might be relevant.

---

### Post by ago on 2007-05-13
What filesystems are you installing on? NTFS or FAT? How big are the virtual drives?

---

### Post by Jerick on 2007-05-13
I'm installing using Vista's NTFS, within its partition.

After changing the home drive to something smaller, and opening the verbose mode, I got the following:
May 13: bio too big device loop6 (1>0) 
ext2-fs: unable to read super block
and then it would repeat but then with ext3-fs, and again, for reiserfs but then this:
resiserfs:loop6:wargning:sh-2006 reads super-block: bread failed (dev[?]loop6, block 2, size 4096)

and one like

init starting pid 8467 console /dev/tty1/ '/bin/sh' 
udevd:delete_path rmdir (/dev/.udev/failed) failed
read-only file system

Now I'm not totally certain what all of this means, but this is happening within the formattting process.

---

### Post by mazingersama on 2007-05-13
My current installation was done in a NTFS filesystem and 4GB System Size, 2GB Home Size and 1 GB Swap Size.
But the previous installation which doesn't work was in a 6GB System Size.
I hope this can help you.

---

### Post by Jerick on 2007-05-13
I'm going to try again but with different sizes.
I have a question. How do I enable the home size setting? It seems disabled for me when I'm reinstalling Wubi.

---

### Post by ago on 2007-05-13
> **Jerick said:**
> I'm going to try again but with different sizes.
I have a question. How do I enable the home size setting? It seems disabled for me when I'm reinstalling Wubi.

that is disabled when you are in reinstallation mode (for security reasons: you do not want to reinstall and override your settings). To be able to change that you have to uninstall and reinstall.

---

### Post by Jerick on 2007-05-13
Thanks. That works for me. (:

---

### Post by ago on 2007-05-14
> **ago said:**
> Can you try to start with a 3GB virtual drive and go up to see if there is a size that will jam the formatter? I will also create a special bulild later on with a change that might be relevant.

Anybody tried the above? I'd like to debug the issue, but I need more info (since I cannot reproduce that on my system).

---

### Post by hollowlife1987 on 2007-05-14
It works fine for me as long as i keep the drive size under 4GB.  At 5GB it halts at 33%

---

### Post by ago on 2007-05-14
> **hollowlife1987 said:**
> It works fine for me as long as i keep the drive size under 4GB.  At 5GB it halts at 33%

Is that an ntfs? Anything peculiar about your disk? Anybody else with the same issue? If you know your way in Linux, can you try to grab a command line (Alt+F2) and see if there is anything abnormal and/or try to format the disk manually?

---

### Post by spitfire23bc on 2007-05-14
I get the same problem: formatting the virtual drive hangs at 33%, and Alt+F4 gave me the following:

```

May 14 12:50:49 main-menu[4681]: (process:5800): 18/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 19/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 20/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 21/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800)
_

```

As for the settings, I had:
     - System Size: 3Gb
     - Home Size: 1Gb
     - Swap Size: 0.5Gb
     - Installation Drive: C:
     - Keyboard: UK English
     - Desktop Environment: Ubuntu


Hope this helps

---

### Post by ago on 2007-05-14
> **spitfire23bc said:**
> I get the same problem: formatting the virtual drive hangs at 33%, and Alt+F4 gave me the following

That to mee simply indicates that you stopped at 21/24th through the formatting. Waiting 3/24th more might have gone through... More interesting is whether it ALWAYS stops at 21 and whether waiting a longer time it ultimately goes through. Also check if your HD has full acceleration (hdparm -I /dev/hda).

---

### Post by pjalegria on 2007-05-14
I have the same problem, 33% hung up....

As for the settings, I had:
- System Size: 4Gb
- Home Size: 2Gb
- Swap Size: 1Gb
- Installation Drive: C:
- Keyboard: UK English
- Desktop Environment: Ubuntu

---

### Post by ago on 2007-05-14
All, can you please let me know: 

1) file system of the installation
2) HD type/raid/anything peculiar
3) How long did you wait at 33% (try to wait 10-20 minutes)
4) Virtual disk sizes (in windows AND in linux, press Alt+F2 to get a shell and browse the /host/wubi/disks folder)
5) Any message visible in Alt+F4
6) Is the wubi folder compressed/fragmented?

There are also a couple of tricks to regenerate the disk images I'd like you to try. Uninstall Wubi, run wubi installer, do NOT reboot. Try one of the methods below to generate the disk images (5GB example below).

[list=a]
[*]get [http://www.kessels.com/JkDefrag/JkDefrag-3.8.zip](http://www.kessels.com/JkDefrag/JkDefrag-3.8.zip) , unzip and run: jkdefrag c:\wubi
[*]Open a dos shell and run: fsutil file createnew C:\wubi\disks\system.virtual.dis 5000000000
[*]Run a program like **qemu-img** ([http://www.h6.dion.ne.jp/~kazuw/qemu-win/qemu-0.9.0-windows.zip](http://www.h6.dion.ne.jp/~kazuw/qemu-win/qemu-0.9.0-windows.zip)) to regenerate the disk images inside c:\wubi\disks. The command is: qemu-img create c:\wubi\disks\system.virtual.disk 4G
[*]Cut and paste the C:\wubi\disks folder to another partition, and then cut and paste it back to C:\wubi. Do this before rebooting. 
[*]If you have a large movie file (or any other file for what matters, except ISO and other virtual disks) of 3+GB, copy it on top of c:\wubi\disks\system.virtual.disk
[*]Simple reinstallation keeping the drives the same size as before
[*]Uninstalling and reinstalling with all drives <= 4GB
[/list]

Reboot and go on with the installation. 

Let me know if any of the above works. That should hopefully help me track down the issue.

---

### Post by JMV290 on 2007-05-14
Last night it got stuck at 33% so I left it like that for about an hour.


I had a 6gb System, 3 gb home, and .5gb swap.

---

### Post by ago on 2007-05-14
I know it's a bit boring, but when you have some time can you try to answer the points above?

---

### Post by JMV290 on 2007-05-14
> **ago said:**
> I know it's a bit boring, but when you have some time can you try to answer the points above?

Okay, sorry. :P


> 
1) file system of the installation
2) HD type/raid/anything peculiar
3) How long did you wait at 33% (try to wait 10-20 minutes)
4) Virtual disk sizes (in windows AND in linux, press Alt+F2 to get a shell and browse the /host/wubi/disks folder)
5) Any message visible in Alt+F4
6) Is the wubi folder compressed/fragmented?


1)My harddrive is NTFS, so I guess it's that.
2)I don't know.  Just a normal harddive for a notebook PC (HP Pavilion)
3)I started it around 10:55 and stopped it around 12:05
4)6GB System, 3 GB Home, .5gb root
5)Hmm, I forget it just gave some progress info I think.
6)It shouldn't be. I defragmented my harddive the night before.

---

### Post by c4software on 2007-05-14
> B) Run a program like qemu-img ([http://www.h6.dion.ne.jp/~kazuw/qemu....0-windows.zip](http://www.h6.dion.ne.jp/~kazuw/qemu....0-windows.zip)) to regenerate the disk images inside c:\wubi\disks. The command is: qemu-img create c:\wubi\disks\system.virtual.disk 4G

I try this solution, the installation process continu but just after formating, the intall request to me the ISO of Ubuntu :/

---

### Post by RawIsWar on 2007-05-14
Hi,

I am new to Ubuntu and to this forum but I have been following this thread with interest after downloading test2 and having the same problem (hanging at 33%). I tried loads of the things mentioned here and have had success by changing the virtual drive size to 4GB. Just wanted to share.....

---

### Post by JMV290 on 2007-05-14
> **RawIsWar said:**
> Hi,

I am new to Ubuntu and to this forum but I have been following this thread with interest after downloading test2 and having the same problem (hanging at 33%). I tried loads of the things mentioned here and have had success by changing the virtual drive size to 4GB. Just wanted to share.....

Total size of 4gb or just the system size?

---

### Post by RawIsWar on 2007-05-14
Sorry, working in Windows right now but i mean the first option in the top left corner when selecting settings at install.

(Hope that helps)

---

### Post by JMV290 on 2007-05-14
> **RawIsWar said:**
> Sorry, working in Windows right now but i mean the first option in the top left corner when selecting settings at install.

(Hope that helps)

It does. 

[IMG]http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/screenshots/wubi-advanced.jpg[/IMG]

---

### Post by ago on 2007-05-14
So far I had a few success report from people reducing the size <= 4GB. That is not necessarily due to size change, it could simply be due to the fact that you are reinstalling. Did anybody try methods A-E with drives larger AND smaller than 4GB? That would help a lot.

---

### Post by pjalegria on 2007-05-14
I already try methods A-E with drive 4GB and still hung up at 33%...dont work

---

### Post by ago on 2007-05-14
> **pjalegria said:**
> I already try methods A-E with drive 4GB and still hung up at 33%...dont work

Do you have a sata disk?

---

### Post by pjalegria on 2007-05-14
No...samsung MP0402H NTFS 40gb on HP Omnibook XE3 GF

---

### Post by ago on 2007-05-14
samsung do sata drives too [http://www.samsung.com/in/products/harddiskdrives/SATA/sr_40gb1.asp](http://www.samsung.com/in/products/harddiskdrives/SATA/sr_40gb1.asp)

---

### Post by pjalegria on 2007-05-14
samsung MP0402H is not SATA...can you help me?

---

### Post by ago on 2007-05-14
So you have an IDE drive on ntfs, you tried all methods suggested (A-E) and still cannot get that to go past 33%. And the drive is not compressed or fragmented

In the shell (Alt+F2) if you type: "hdparm -I /dev/hda" do you see an asterisk close to udma?

edit that's an "i" capitalized, and it's udma

---

### Post by pjalegria on 2007-05-14
I have to install again to see that?, i already made the instalation +/- 10 times, im afraid to lose my XP instalation...

---

### Post by ago on 2007-05-14
Don't worry pjalegria, you have been very useful. Unfortunately I cannot reproduce the error on my machine and I have to rely on other people reports which makes everything more difficult. I hope some experienced linux user gets the same error so he can help me out figure the issue.

---

### Post by c4software on 2007-05-15
So, i try with the tools Contig if its work i edit my message under Ubuntu :P

(Its Very Slow to Make files contiguous always on file home.virtual.disk,and now Swap files, and for finish System :D)

Its Works after install the system its UP :D

---

### Post by ago on 2007-05-15
We are considering shipping jkdefrag:

[http://www.kessels.com/JkDefrag/JkDefrag-3.8.zip](http://www.kessels.com/JkDefrag/JkDefrag-3.8.zip)

If you get stuck at 33%, can you pls 

1 uninstal wubi
2 install wubi againl (but do not reboot)
3 unzip 
4 run: jkdefrag c:\wubi
5 reboot

Pls report back if it works or not

---

### Post by c4software on 2007-05-15
I try Jkdefrag, (other method like contig are work one time :() now formating frezze again at 33%)

---

### Post by pjalegria on 2007-05-15
Same were....:(

---

### Post by ago on 2007-05-15
Can you pls confirm that when you defragmenting with contig it works and with jkdefrag it does not? (Possibly doing 2 more trials)?

---

### Post by Antimethod on 2007-05-15
I tried to defragmet the wubi folder with jkdefrag
it finished
i restarted but it stopped at 16% and prompted an error like critical instalation error...with a red background

---

### Post by ago on 2007-05-15
> **Antimethod said:**
> i restarted but it stopped at 16% and prompted an error like critical instalation error...with a red background

That's a different issue. Sometimes when the images are created they get allocated and old block of disk. It may happen that that block coincides with an old virtual disk. This tricks lupin to believe that the image is not vergin, and for security reasons lupin will only install onto a sparkling new image... In short you need to repeat the procedure possibly removing the system file and placing in there some large file. This is a known bug [https://bugs.launchpad.net/wubi/+bug/113707](https://bugs.launchpad.net/wubi/+bug/113707) but a different one from the 33% one.

---

### Post by c4software on 2007-05-15
so, i make clean install (in first freeze at 33%).

First test with Contig (after a long long time...) i reboot and nothing always freeze at 33%.

Second test with Jdefreg (after a long time for defrag) i reboot and its same freeze at 33%

But this morning, the format works one time with Contig... But now its doesn't work :X

---

### Post by pjalegria on 2007-05-15
here can i donwnload "contig" to try?

---

### Post by pjalegria on 2007-05-15
I think Wubi dont work on my Laptop :( ... I give up.... :(

---

### Post by ago on 2007-05-15
[http://download.sysinternals.com/Files/Contig.zip](http://download.sysinternals.com/Files/Contig.zip)

c4software, as I suspected that might not be related to fragmentation after all, the fact that it worked with contig might have been a case. 

Can you try to use another large file and copy it on top of system.virtual.disk? That will make sure that the file is created correctly. Any avi/dvx movie will do nicely. 500MB+ is also ok, that will fail later on because of lack of space, but now I am only interested in seeing if the formatting goes through not in the actual installation.

---

### Post by ago on 2007-05-15
> **pjalegria said:**
> I think Wubi dont work on my Laptop :( ... I give up.... :(

Come back in a few days, when you do not see the "beta", it means we have fixed this issue (and the grldr 17 one)

---

### Post by pjalegria on 2007-05-15
Ok...tanks

Ill be back...:)

---

### Post by c4software on 2007-05-15
so, I copy a movie and the result its the same :( Format Freeze at 33%

---

### Post by foxtrott on 2007-05-15
Hi,
my hard disk is a fujitsu MHT2040AT.
My laptop is a Fujitsu siemens Amilo-EN Celeron 2.4 256Mo ram.

-hdparm -I >> NTFS *udma5 >> so it should be ok
-partitions sizes: 4gb /0.5Gb/0.5Gb >> so it should be ok

-jkdefrag done before reboot but no effect
-contig done before reboot but no effect
-virtual drives regenerated but no efect

I tried all you said.

but the install of ubuntu stops again at 33%.
->alt+f4>> main menu 4634: process 5745: 27/32

Please help me!!

---

### Post by ago on 2007-05-15
> **foxtrott said:**
> 
but the install of ubuntu stops again at 33%.
->alt+f4>> main menu 4634: process 5745: 27/32

Please help me!!

Can you monitor the progress from alt+f4 and see it proceeds very slowly or if it stops at 27?

---

### Post by foxtrott on 2007-05-15
it stops every time at 27.
sometimes I have waited more 1 hour to be sure.

---

### Post by ago on 2007-05-15
Uninstall and install again (defrag just to be sure). Wait for it to jam. Grab a shell (Alt+F2)

ps ax | grep ext  #list of running process which are formatting virtual disks, there should be one formatting /dev/loop7
kill -15 5745   #use the process number here it will change every time, assuming 5745
kill -9 5745
ps ax|grep ext #check we killed it


#check that all virtual disks are of the right size
ls -al /host/wubi/disks 

#format the firtual disk manually in verbose mode
mkfs.ext3 -v /dev/loop7

---

### Post by pjalegria on 2007-05-15
It sems very dificult...

---

### Post by ago on 2007-05-15
I have to understand what is happening since I cannot reproduce. I will turn on verbose mode in next build by default.

---

### Post by foxtrott on 2007-05-15
the process doesn't want to be killed
kill commands no generate errors but the process is still alive :(

---

### Post by ...Max... on 2007-05-15
May I add my voice to foxtrot's?

- Old Sony VAIO UltraSlim (circa 2000), IBM DJSA-200 HDD
- mkfs.ext3 hangs up on /dev/loop7 in state=D, cannot be killed
- Place in the log apparently depends on vdisk size and fragmentation state
- I tried to vary the disk sizes and pick either of the available 2 NTFS partitions for install
- Tried COMPLETE defragmentation with contig, same result

I don't absolutely need a Wubi install because my purpose is to replace Windows completely on a CD-less laptop but I'll try to hang on and get this approach through to completion, if any.

Regards,
...Max...

---

### Post by ago on 2007-05-15
can you try [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.8.exe) (no high hopes)

---

### Post by pjalegria on 2007-05-15
What is the diference????

---

### Post by pjalegria on 2007-05-15
Same problem...33% hung up...:(

---

### Post by DT North on 2007-05-15
Just tried the new version after experiencing the exact same problem of freezing at 33%, this time it froze right after the "No RAID disks" line

---

### Post by foxtrott on 2007-05-16
same result with the new release!!!

---

### Post by ago on 2007-05-16
> **pjalegria said:**
> What is the diference????

There is a new algorithm to generate the virtual disks, and a verbose mode during formatting. If you look into /var/log/syslog you should be able to get more detailed info. 

Alt+F2
nano /var/log/syslog

Look for hints. Try to kill the offending process ("ps ax" for a list of process, you are looking for mkfs)

---

### Post by ago on 2007-05-16
> **DT North said:**
> this time it froze right after the "No RAID disks" line

That is a different issue then. Uninstall and reinstall. If it jams again please provide more detailed info.

---

### Post by c4software on 2007-05-16
I try again the install with th new intaller and its works this time :D

---

### Post by foxtrott on 2007-05-16
i have retried again and i could see in the syslog these lines:
>mounting /dev/loop7 on target$
>invalid argument

i think the disk is not mounted and it's for that the virtual drives can be formatted.

I'm wrong??

---

### Post by ago on 2007-05-16
> **foxtrott said:**
> i have retried again and i could see in the syslog these lines:
>mounting /dev/loop7 on target$
>invalid argument

i think the disk is not mounted and it's for that the virtual drives can be formatted.

I'm wrong??

That might be ok, I try to mount the virtual disk to make sure I do not format a non-vergin file, when the file is actually vergin that fails (which is expected).  This is not where it jams, is it? There should be other lines AFTER that, in particular something like: "Formatting root device: /dev/loop7"

---

### Post by ago on 2007-05-16
> **c4software said:**
> I try again the install with th new intaller and its works this time :D

That might be a random result. Can you try again?

---

### Post by foxtrott on 2007-05-16
> **ago said:**
> That might be ok, I try to mount the virtual disk to make sure I do not format a non-vergin file, when the file is actually vergin that fails (which is expected).  This is not where it jams, is it? There should be other lines AFTER that, in particular something like: "Formatting root device: /dev/loop7"

Yes this is not where it jams. 


> **c4software said:**
> I try again the install with th new intaller and its works this time :D

you'r so lucky. I'm envious :)

---

### Post by c4software on 2007-05-16
it certainly a random result because yesterday Wubi works great, i retry 1 hours later and its doesn't work, i retry today and its work i changed nothing exept the Wubi intaller

---

### Post by Antimethod on 2007-05-16
I installed ubuntu with Wubi-7.04-minefield0.8.exe and it worked just fine.
thank you!

---

### Post by pjalegria on 2007-05-16
"NO RAID DISK"
" Couldnot mount sys file or directory"... something like that, and then 33% hung up...:(

---

### Post by k0zy on 2007-05-16
I have exactly the same issue.

I tried with Wubi-7.04-minefield0.8.exe, but still no luck.

---

### Post by pjalegria on 2007-05-16
I think we are DOOM...there is no way to WUBI work well...:(

---

### Post by ago on 2007-05-17
I have opened an official bug report [https://bugs.launchpad.net/lupin/+bug/115217](https://bugs.launchpad.net/lupin/+bug/115217) . If you think you have a good explanation feel free to post in there.

---

### Post by c4software on 2007-05-17
So i will try again. I try on another machine, after a long long long long time (with minefield0.8) the install was a success, i just wait more than an hour on 33%

---

### Post by emoticonartist on 2007-05-17
I've tried to install Wubi several times  but still, I always get stuck at the formatting virtual disk screen exactly at 33%.  Since I'm running this on a Thinkpad X30 (optical drive-less) I figured Wubi would be worth a try!

What I've done after installing and not rebooting (several times):

So far I've defragmented the C:\wubi directory w/ JkDefrag.
I've reinstalled on top of Wubi being priorly installed, but w/ a 3GB system disk size, and both home & swap at 0.5.
Done the same install settings from a fresh install of Wubi.
Ran Contig on the all the virtual disk sizes.
Wubi folder is not compressed/fragmented.
And I've tried the qemi method of recreated the virtual disks.

So far all the options have not worked.  

Here's my system:

Thinkpad X30, NTFS
Ultra ATA Storage Controller
(Needed?) Primary & Secondary channels: Standard IDE ATA/ATAPI controllers

When stuck at 33%, I go to Alt F4 and get something like this (took this copy of an earlier post):

May 14 12:50:49 main-menu[4681]: (process:5800): 18/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 19/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 20/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (process:5800): 21/24
May 14 12:50:49 main-menu[4681]: (process:5800): ^H^H^H^H^H
May 14 12:50:49 main-menu[4681]: (proce **Mine actually freezes in the middle like this**

I figured it might take more than hour...so I left it on overnight for 7 hours and still nothing.
Also, when I open a dos shell in Alt F2 and try to type in hdparm -I/dev/hda, it doesn't show anything (unless I'm supposed to put a space after the -I /dev/hda).

I'm not giving up, but I figured I'd let you know what I've been doing.
I haven't ventured in going above 4GB in the system disk setting, but figured that wouldn't work as well even when set at 3GB.

Sorry for the long post everyone, but I'd rather be concise!

---

### Post by ago on 2007-05-18
Very useful, thanks.

What you can do is grab a shell either before or after the jam with Alt+F2. Then kill the process that is formatting the virtual disk and try to format the image with manual commands. Check the images from the shell, the free space and so on, hopefuly something irregular will be noticeable.

---

### Post by polkaishot on 2007-05-18
I had the same problem and it worked at 4gb.

---

### Post by emoticonartist on 2007-05-18
Hi Ago,

I'll try the kill process when I have the chance.

I notice that everyone seems to have changed the home disk setting to 4GB and had it installed no problems.
I've done that too, changed it from default of 6GB to 4GB, and even tried it under 3GB but still nothing!
It seems most people's hard drives are SATA's, but I wonder if the issue could be that I'm using a Ultra ATA storage?

Anyways, I'll let you know how it goes later on.

---

### Post by pjalegria on 2007-05-18
I dont understand...I try on other PC and it works fine at 1ª time,,,i have another problem because the PC is very old, but Wubi installation works fine...

Why doesnt work in my laptop....:(

---

### Post by ago on 2007-05-18
It might be an ntfs-3g bug. But as mentioned I cannot reproduce that myself, therefore it is quite difficult for me to debug. I hope that some experienced linux user gets the same bug, so he can help us understand the issue from command line. The idea is to grab a shell (alt+f2) as early as possible and monitor the processes to see what happens, it might be a good idea to kill ext2 before it hangs and issue the command manually

---

### Post by pjalegria on 2007-05-19
I am using Raxo Perfect Disk to defrag my HD, its possible that is making this problem????

---

### Post by jpierce on 2007-05-20
I'm actually getting a "KILLED" coming through the graphical formatting application that stops the formatting, and it does it immediately at the beginning of the process. Any idea why the OS would kill the process.

PIII 800mhz
40 gig WD enhanced IDE
98 megs ram
ATI video

---

### Post by jpierce on 2007-05-20
Forgot, I'm not NTFS but FAT32

---

### Post by tuxcantfly on 2007-05-20
stickying thread, seems like this is a widespread issue...

**~~~Potential Fix???~~~**

We're getting the feeling that this may have something to do with the Wubi disk image generation code, so I've generated some virtual disks with the Linux version, Lubi ([http://ubuntuforums.org/showthread.php?p=2648900](http://ubuntuforums.org/showthread.php?p=2648900)) which may fix this issue on some computers:

1. Run the Wubi installer

2. Delete anything from C:\wubi\disks (the system.virtual.disk, home.virtual.disk, and swap.virtual.disk files)

3. Download the file from [http://cutlersoftware.com/ubuntusetup/vdisks.exe](http://cutlersoftware.com/ubuntusetup/vdisks.exe) that's a 7-zip self-extractor with the 3 virtual disks

4. Have it extract the files to C:\wubi\disks then check to make sure that system.virtual.disk, home.virtual.disk, and swap.virtual.disk are there

5. Reboot, and give it 30-45 min. for the formatting virtual disks portion, if there's no activity in that time, report it here, but if this does work, make sure to tell us so we can have this fixed in the next version...

---

### Post by fredfr on 2007-05-22
I tried the "Potential Fix" 
It worked fine and resolve my virtual disk problem on two different computer wich had this problem.
Sorry for my poor english
Hope this could help

---

### Post by pjalegria on 2007-05-22
I already have solved my problem, i have installed Ubuntu in my pc...without windows;)

---

### Post by John Duff on 2007-05-22
Hi,

The *Potential Fix* also fixed my problem. I always stayed stucked at 33%, but with that fix it worked fine, although I had to wait for 30-45 minutes as notified. Kubuntu installed well. I tried to uninstall it and install Ubuntu without the fix, but it didn't work, as usual. So tomorrow I'm going to try to install Ubuntu with that potential fix to see if it was just luck. ;)

---

### Post by tuxcantfly on 2007-05-22
**~~~Update on "Potential Fix" post~~~**

It seems like the temporary "fix" I posted appears to be working for some... We're trying to determine whether or not the issue is due to issues in the Wubi virtual disk generation techniques, or simply because of the smaller size of the disk images (they were only 4 GB), so could some users, especially those for whom the "potential fix" worked, try out these larger virtual disks to help diagnose the problem?

larger preformatted disks (10GB system.virtual.disk, 10GB home.virtual.disk, 1GB swap.virtual.disk) download the 3MB self-extractor at [http://www.cutlersoftware.com/ubuntusetup/vdisks10g.exe](http://www.cutlersoftware.com/ubuntusetup/vdisks10g.exe) and follow the instructions in my post at [http://ubuntuforums.org/showthread.php?p=2690574#post2690574](http://ubuntuforums.org/showthread.php?p=2690574#post2690574) for using them, note that it will likely take longer to format them since they're larger files, it could take up to an hour or two depending on hard drive speed.

---

### Post by rohan000 on 2007-05-22
The Potential Fix didn't work for me, after about 75 minutes it was still stuck at 33% at 21/29.
I will try it again and wait longer.

---

### Post by jpierce on 2007-05-23
I too loaded Ubuntu directly onto my whole drive after I'd trashed the WX installation.  It works fine but I'm still persuing the WUBI route on another machine.  If this gets ironed out I believe it will truly be a "Disruptive" technology.

---

### Post by stevezygote on 2007-05-23
I tried what was said in this thread. I reduced the virtual drive to 4Gig. It STILL hung at 33%. I h ave a Maxtor 4R060J0 that's 80GIG, partitioned from the factory with a 5GIG FAT and the rest NFST. I have a 2.2Ghz Cerelon with .5 GIG of RAM. Still it hangs at 33%. I end up having to forcably reboot. Any help would be appreciated.

ADDENDUM: I read through the thread some more and noticed someone had posted instructions to use a vidisk.exe. I tried to download it and it wouldn't even start. In fact I had problems stopping it. I am using FDM.

---

### Post by ago on 2007-05-23
Did you try [http://cutlersoftware.com/ubuntusetup/vdisks.exe](http://cutlersoftware.com/ubuntusetup/vdisks.exe) or [http://www.cutlersoftware.com/ubuntusetup/vdisks10g.exe](http://www.cutlersoftware.com/ubuntusetup/vdisks10g.exe) (assumes 20GB free)?

Also when you get stacked can you get to a shell with alt+f2 and run commands or is it frozen?

---

### Post by jimbo99 on 2007-05-23
I have a compaq presario r3000 notebook with a brand new 60gig HDD that I put in and reinstalled XP on less than a week ago.  I have done nothing with it but view the web and chat.

I got stuck at the 33% also until I reduced the virtual disk size to 4 gig.  At this time it formatted, apparently, then after that it got stuck at 83%.

This is a brand new IDE HDD (not SATA).

If I hit ALT+F4 I have various messages about bio too big device loop6 for various file system types.

It is sitting at 83% now.

It would be exceptional if you could resolve this issue as you would put to bed your major issue with this product.

Any real reason you chose the alternate iso instead of just the regular one they use for ubuntu?

---

### Post by ago on 2007-05-23
> **jimbo99 said:**
> 
It would be exceptional if you could resolve this issue as you would put to bed your major issue with this product.
The problem with that is that we cannot reproduce the issue on our side and hence debugging is problematic. We hope that some of the more experienced users can help us out by pinpointing the issue. It might also be an ntfs-3g bug. For the home virtual disk, change the size to 0.5, or even to 0.

> Any real reason you chose the alternate iso instead of just the regular one they use for ubuntu?
Because the alternate-iso comes with d-i installer which in turns supports unattended installation. Using the live iso requires a different version of ubiquity. Next version that will ship with Ubuntu 7.10 should work with the live iso as well.

---

### Post by stevezygote on 2007-05-23
Wubi selected the file for me. I had no say in the matter. It took all of 14 hours to download it! Eeeek. And I just can't resolve the issue so I think I'm deep sixing it. I have installed WmPlayer and the Debian windowed version to experience it. Maybe I'll stick with that. I have an old 333Mhz machine with only 5.2 GIG of HDD and something like a meg of RAM that I installed an older version of Mandrake on but it was as slow as treacle on a cold day....

---

### Post by ago on 2007-05-23
> **stevezygote said:**
> Wubi selected the file for me. I had no say in the matter.
If you reinstall you cannot change the home virtual disk (to preserve data that might be in there). You have to uninstall, install again and press on settings.

> It took all of 14 hours to download it! Eeeek.
You can download the ALTERNATE ISO manually and place it in the same folder as wubi.

---

### Post by jimbo99 on 2007-05-23
I downloaded the vdisks.exe and tried the install as recommended.  I extracted the virtual disks to the root of my c: and moved them into the proper directory.

What I think is missing is that first at 33% the formatting of ONE (1) Uno, a single one, of the virtual disks fail.  When you create it at a smaller size it will format that and continue to the next virtual disk.  Then the next.  It seems to stop at 83% because it is attempting to format another.

When I replaced the virtual disks with the ones provided all 3 worked.

As the unattended install continued it told me it was detecting hardware.  That went fine till it  hit the networking components.  Then it prompted me with a red screen and a message that the network portion had problems.  No idea of how useful ubuntu would be without networking.  Hopefully it copied necessary files anyway and configured everything with some form of defaults so that I can go back and fix the rest.

After I hit continue it continues and has been progressing through the installer error free.

I can't also imagine using only a 4 gig drive.  So, I've downloaded the 10gig images.  I'll go through this one more time after I see the installer complete and boot without any other serious errors.

BTW, I love ubuntu.  I show it off to every customer that comes into my store.  They get to see some really amazing things as my 24" wide screen HD LDC makes ubuntu and beryl look amazing.  The more we all advertise this stuff to average consumers the more they'll understand they have quality alternatives to the spyware and DRM infested Vista.:popcorn:

---

### Post by jimbo99 on 2007-05-23
I managed to get a solid install of ubuntu w/ wubi earlier today and after doing a bit of configuring I decided that I wanted a larger virtual disk.  The 4gig space was just not enough.  Could never be enough for anyone unless they want to run a gimped system or they are not serious about ubuntu.

What I did was manually delete all files and folders except the .iso file.  I left that in the directory it was in before.  I've done this before without problems.

Then I reran the installer.  I chose not to reboot.  I deleted the virtual disks.  I then extracted the 10gig pre-formatted virtual disks and moved them to the proper directory.  Upon reboot the system began to reinstall.

During this attempt at using the 10 gig file it stopped at 33% and would not continue.  I attempted to kill the formatting process to do it manually but nothing would kill the process.

I then rebooted, and reran the installer and this time I'm not erasing the pre-formatted virtual disks.  I'm just changing the size and letting it go from there.  During this I chose advanced and set the drive size to 10gigs. I then clicked next.  At this time I got the message "Error opening file for writing:  C:\wubi\license.txt...click abort to stop, etc. etc.".

I chose to ignore it.  The installer continued and prompted me to reboot.

This time I did.

When it started up I continued the boot from the ubuntu option and it copied some files and then stopped at the 33%.

When I looked last time using alt+f4 it was stopped at 73/79.  This time it is stopped at 65/79.

What this means is that I have to go back to the 4gig size and just not use the set up for anything real--until you guys work out the exact problem.

Also, in reading through these threads it has become abundantly clear that the issues are most likely to occur on notebooks.  It doesn't seem to matter which drive manufacturer or which notebook manufacturer.  Maybe the chipset for the IDE/SATA is in question so it would be nice to know the exact chipset and revision that each of these notebooks is using.

---

### Post by jimbo99 on 2007-05-23
I performed the install using the 4gig pre-formatted virtual disks to try to get back the Ubuntu install I had earlier.  This time it appeared to perform all functions of the install properly but upon reboot into the final OS it locks only a fraction of the way in.

I exited the graphical progression (of the boot process) and finally got a message about stdin:  error 0
then some info about mod probe.

Then mounting messages telling me /root/dev on /dev.static/dev failed:  no such file or directory.

Repeats that for /sys and /proc

busybox built in shell loads and i'm at initramfs.

Going to wipe and do it again.

---

### Post by lokemo on 2007-05-24
Wonderful, the Potential Fix solved my problem ! Thank you !

Note that a first try failed during the installation (during the unpacking of the packages). I uninstalled wubi, reinstalled, ran vdisk, rebooted and it worked. The only difference is that at the first try, I was not connected to the network when I rebooted.

---

### Post by ago on 2007-05-24
> **jimbo99 said:**
> During this attempt at using the 10 gig file it stopped at 33% and would not continue.

Was that on an ntfs partition or a fat one?

When it locks can you try to kill the process either with Ctrl+c or with kill -9?

Can you then try to run the command manually? 

mkfs.ext3 -v -c /dev/loop7 

You may also want to use the -k flags with mkfs (slower).

---

### Post by Temujin_12 on 2007-05-24
> **ago said:**
> If you reinstall you cannot change the home virtual disk (to preserve data that might be in there). You have to uninstall, install again and press on settings.


You can download the ALTERNATE ISO manually and place it in the same folder as wubi.

On this, it would be nice if the uninstaller gave an option to keep the ISO around (explaining that if it is removed it will have to be downloaded again).  Just an idea.

BTW: I'm past the 33% hang and in a working Kubuntu system by using [http://cutlersoftware.com/ubuntusetu...nefield1.0.exe](http://cutlersoftware.com/ubuntusetu...nefield1.0.exe) choosing a 4GB partition instead of the default 6GB. :p  This works for me since all I'm using it for is development (can't stand developing in a Windows environment), but if I needed it for more than just that then 4GB probably wouldn't be enough.

---

### Post by ago on 2007-05-24
> **Temujin_12 said:**
> 
BTW: I'm past the 33% hang and in a working Kubuntu system by using [http://cutlersoftware.com/ubuntusetu...nefield1.0.exe](http://cutlersoftware.com/ubuntusetu...nefield1.0.exe) choosing a 4GB partition instead of the default 6GB. :p  This works for me since all I'm using it for is development (can't stand developing in a Windows environment), but if I needed it for more than just that then 4GB probably wouldn't be enough.

Well if you are a developer you probably know your way around linux, we cannot reproduce the 33% issue on our side and need skilled users to help us pinpoint the issue. If you happen to have time to waste and manage to find out the underlying reason for the freeze, that would help us a LOT.

---

### Post by HugoMelo on 2007-05-24
I will try to comment my tests..

First of all:
1) file system of the installation
- NTFS

2) HD type/raid/anything peculiar
- Western Digital (40GB) IDE with more than 15GB free space.

3) How long did you wait at 33% (try to wait 10-20 minutes)
- I waited more than 24hs, but almost every trying was waiting 10-20 minutes.
- When it worked was waiting less than 5 minutes.

4) Virtual disk sizes (in windows AND in linux, press Alt+F2 to get a shell and browse the /host/wubi/disks folder)
All access to the ntfs partition stays waiting, but you can stop it with ctrl+c. Only mkfs cannot be stopped.
Some commands like "dmesg" and "cat syslog"  blocked the shell and turned unable to close. 
5) Any message visible in Alt+F4
Each trying it stops at one point. All showing a state X/Y of formatting process. I will explain better below..
6) Is the wubi folder compressed/fragmented?
No
Now i am testing using the minefield0.8 version and:
With 3GB and 4GB settings it worked fine. I have tried 2 times for each.
Later, with 5, 6 or 10GB the formatting stays freezed.

before, I tested using a ubuntu-desktop iso cd.
I booted and installed ntfs-3g packages.
Mounted the /dev/sda1 (windows partition) with -t ntfs-3g
losetup /dev/loop2 /mnt/wubi/disks/system.disk
and mkfs.ext3 -c /dev/loop2
Any times it worked, others It all the desktop appeared freezed..
asap i will send more info..

---

### Post by jimbo99 on 2007-05-24
> **ago said:**
> Was that on an ntfs partition or a fat one?

When it locks can you try to kill the process either with Ctrl+c or with kill -9?

Can you then try to run the command manually? 

mkfs.ext3 -v -c /dev/loop7 

You may also want to use the -k flags with mkfs (slower).

It is an NTFS partition.  I was able to get it to work with the 4gig pre-formatted earlier.  It is the 10gig that didn't work which forced me to go back to the 4gig version.

I've tried alt+f4 and was UNABLE to kill the process.  I tried repeatedly with every variation on killing the process that I know of.  Killall,   -9, -15, ctrl+c, ctrl+break No luck.

I could not get mkfs to work because I couldn't get the prior command to terminate.

Keep in mind my attempts at a 4gig generated from the windows installer didn't work.  I downloaded and  used your 4gig pre-formatted and got that to work.  Then I undid everything because I was happy with the install, just not with the limited amount of space.  I then downloaded and used the 10gig version of the pre-formatted files.

Also, keep in mind that you provide 3 pre-formatted virtual disks but when the installer creates them it only creates 2 for me.

Continuing on in this tale.  The first pre-formatted 4 gig attempt worked.  Then the 10gig pre-formatted failed.  The subsequent reinstall using the pre-formatted 4 gig worked but I couldn't boot into Linux like I could the first time.

I'm going to try again but this time I'm going to delete the grldr file first.  Not likely this will affect the issue, but hey, worth a try.

Your installer also creates the two virtual disk files slightly larger than the ones that you provide with your pre-formatted ones.

---

### Post by jimbo99 on 2007-05-24
A bit of bad new.  After attempting again with the 4gig pre-formatted virtual disks I was successful in getting the install to complete.  I then rebooted.  At the menu I chose the ubuntu men item to boot from.

Ubuntu went past the graphical progress bar and began the desktop start up.  I received the rectangular bar with the service (etc) icons and the start up sound but only made it so far as the brown default desktop background.  No icons. I did have a movable mouse cursor.

I let this sit for a while and the drive light came on a few times (one time for quite a while).  Then it went off.  The mouse cursor continued to work, but I was forced to power off.

After rebooting the system continued to reboot over and over at the point where it would access the boot loader.

I removed the notebook  HDD and attached it to a nice USB/IDE device (not an enclosure--it is a device with notebook IDE connector on one side and a standard IDE connector on the other which at the end of the cable has a USB plug) and connect it to a windows XP box.  The drive showed up in the list of drives but there's nothing on the drive to work with.  Zero bytes used and zero bytes free.

Not a big loss for me as the system was pretty much a clean install onto a new 60 gig drive.  I'll just boot with ubuntu 7.04 and see if I can get it up and running that way.  I'm going to then erase it and go back to windows xp and try again with wubi.

---

### Post by jimbo99 on 2007-05-24
I was able to recover the drive by attaching it to the machine via another IDE cable that I have for notebooks that attach directly to the IDE port on a desktop motherboard and then rebooting.  The initial start up ran checkdisk on it and found lots of orphaned files.  It automatically correct them.  I was able to then put the notebook drive back in notebook computer and boot to windows normally.

This'll put an end, I guess, to the testing of wubi for a while.  Not that I can't afford to risk the loss as it would be minimal due to this notebook just being a spare of many I have laying around.  I just don't want to have to start over and over and over.  Going to far back in the start over process would just be too consuming for me.

---

### Post by jimbo99 on 2007-05-25
I have several notebooks here so this morning, as I had a couple hours to do with what I wanted, I chose to do a wubi install on it.

I downloaded the test2 and confirmed I still had my .iso file.  Then I ran the installer without the pre-formatted virtuals.

This went well.  I rebooted and choose ubuntu from the boot menu.

It ran for a very short while.  Just after it displayed the message about no raids, it stopped.  I let it sit for some time and then it came back with a series of messages.  One stated that it couldn't find the .iso file.  Then some other message about loop3 or something like that.

I realized that when I had problems with my NTFS partitions if a chkdsk hadn't been completed (and was needed as Windows had flagged it) then ntfs-3g would refuse to mount the volume.

So I booted into windows, and scheduled a chkdsk.

Windows rebooted and ran the chkdsk, found, and recovered several minor errors.

I then rebooted and choose the ubuntu option.

But unfortunately it stopped at roughly the same spot.  I let it sit for a while waiting to see if I got the same messages.  I did not.  The messages were different, but about as useful.

So, no luck on an HP ZV5000 notebook.

---

### Post by jimbo99 on 2007-05-27
I successfully installed Ubuntu through WUBI on a dell Inspiron 5100 notebook, but I had to use the 4gig pre-formatted virtual disks.  The 10gig ones would not work.  The non-pre-formatted ones would not work.  Again, the installer only created 2 of the 3 virtual disks.

I also successfully installed Ubuntu through WUBI on a generic clone p4 2.8.  I had to also use the pre-formatted 4gig as the 10gig wouldn't work, not even the pre-formatted ones.  Also note that during the attempts and reboots periodically I'd get frustrated and pull the power plug.   Typically I'd do this when I forgot to select the Ubuntu menu item at boot.

When doing this I found that the installer wouldn't continue until I entered windows XP and ran a simple chkdsk.  This would remove the flag that the volume was not shut down properly and hence NTFS-3g would not mount the NTFS partition so it was impossible to complete the install.  After the chkdsk everything installed properly.

Hope that made sense.  I'm a bit tired.

---

### Post by bentura on 2007-05-27
Hello there.

I to am having a problem installing Wubi.

Im running a Dell Latitude C400 996Mhz (1000mhz) CPU, 256 RAM

I am stacking at 33% and after pressing ALT + F4 its stopped at 21/32 but this differs,  the last time i tried it said: 

main-menu[4417]:Process 5536:27/42.  sits there like that for over an hour.

Ive tried using the vdisks images, def refragging using jkdefrag and the windows defrag tool and ran chkdsk on my system.

Virtual disks sizes. 4 to 7 (only got a 18GB drive so cant go any higher really)

I havent got a CD Drive for the laptop but i have manged to install Ubuntu by installing it on a hard drive in a Dell D400 and then plugging that drive into me C400.

I also get an error right after the NO RAID DISKS message about not being able to mount /sys as the file cannot be found and then another error about no being able to create /sys due to some permission error.

And sometimes, a red error box appears saying it cannot complete the next step.. that is mouting the CD image.

---

### Post by ago on 2007-05-27
We had a few good tips, we'll try to get a build out soon that will hopefully address those issues.

---

### Post by ago on 2007-05-28
> **ago said:**
> We had a few good tips, we'll try to get a build out soon that will hopefully address those issues.

Ok here it is our preliminary build [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

Please do NOT use the usual tricks above, do select large images, the intention is to grill the new build, it should be able to work as is without extra tricks. 

Many thanks to Szabolcs that pointed us in the right direction.

---

### Post by spaceship9 on 2007-05-28
I know you already made the minefield but here's my report from using the latest beta

created system 10 GB, home 5 GB, swap 2 GB. used ubuntu studio.
PATA 300 GB Seagate drive.
stuck at 33%

what i did to work (dunno what parts "did it" so here's everything")
used QEMU to make a 10 GB file over the old one, and used QEMU to make another 5 GB home over the old.
Defragmented wit jkdefrag.
same hard drive.
worked fine(ish)

I'm testing the Minefield right now.. I'll edit this post after its done

EDIT:
tested minefield
slightly slower formating then the above way I did, however it worked... and over all its faster because I didn't need to do all the extra stuff
same file structure
10 GB system, 5 GB home, 2 GB swap.
during boot however, Ubuntu couldn't find a "extra.virtual.drive"...

---

### Post by ago on 2007-05-29
> **spaceship9 said:**
> 
EDIT:
tested minefield
slightly slower formating then the above way I did, however it worked... and over all its faster because I didn't need to do all the extra stuff
same file structure
10 GB system, 5 GB home, 2 GB swap.
during boot however, Ubuntu couldn't find a "extra.virtual.drive"...

I am glad about that. As for the extra.virtual.drive, that is normal. It looks for it in case you want to add one, but it's optional.

---

### Post by bentura on 2007-05-29
Fantastic.  Minefield has worked fine for me, no issues (so far) what so eva.

nice one guys, thanks for getting it right and fixed.

Will keep looking and playin.

---

### Post by bentura on 2007-05-29
Oooo, i do have one problem.  My USB wireless adapter is not getting recognised.

Ill have a look at it myself, but one quick question?  Would it make a difference being on USB 1.1?

---

### Post by ago on 2007-05-29
Have a look in the general ubuntu forum for that

---

### Post by bentura on 2007-05-29
Yeah thats cool.  Thanks again.

---

### Post by ago on 2007-05-29
New release ([http://ubuntuforums.org/showthread.php?t=458607](http://ubuntuforums.org/showthread.php?t=458607) ) now should take care of "error 33%".

---

### Post by Vadi on 2007-05-30
I've had the 33% problem with the test2 release, but then again, I set the system size to 5gb while I only have 5.5gb free, so I think that was the issue.

I've installed the test3 version today, with all sizes at default, but for some reason, it didn't modify boot.ini to include Linux. Is there any way I can get it off from where?

Edit: I guess I'll try re-installing the whole thing again.

---

