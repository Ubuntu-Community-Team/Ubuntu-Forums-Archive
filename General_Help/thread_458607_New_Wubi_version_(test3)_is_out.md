---
title: "New Wubi version (test3) is out"
date: 2007-05-29
forum: General Help
---

### Post by ago on 2007-05-29
We have released a new wubi version (Wubi-7.04-test3). You can get it from our website [www.wubi-installer.org](www.wubi-installer.org). 

[http://cutlersoftware.com/ubuntusetup/latest.html](http://cutlersoftware.com/ubuntusetup/latest.html)

That includes several bug fixes which should cover most people that had problems with previous release: grldr fixes, 33% freeze fixes, reboot issues, raid1/0...

---

### Post by yapel on 2007-05-29
Well, Test 3 fails to work on my IBM Thinkpad R40 in exactly the same way as Test 2, i.e. cannot find grldr! Any quick fix?

---

### Post by jimbo99 on 2007-05-29
On my HP Pavillion zx5000 after removing the prior install and reinstalling  using a 10gig virtual disk size the system hangs after "No RAID disks".  Then it dumps a bunch of messages about:

Check root= bootarg cat /proc/cmdline
or missing modules, devices:  cat /proc/modules ls /dev
ALERT! /media/hosts/wubi/install/install.virtual.disk does not exist.  Dropping to a shell!

Then some info about busybox and then a shell prompt.

Upon looking at the c:\wubi\install the install.virtual.disk is there but it is only 100k.

I also see you created some metalink files for various Ubuntu flavors.

---

### Post by psayre23 on 2007-05-29
Is there anyway to upgrade without a reinstall? I keep getting loop7 errors on shutdown and need to fix it.

---

### Post by jimbo99 on 2007-05-29
I have typically moved my .iso file and then manually deleted the folders and just ran the test# to reinstall.

After encountring the problem above I decided to:

1) remove the share from the c: in XP.
2) Move the .iso to the desktop
3) Use the test3 to do an uninstall.
4) schedule a checkdisk
5) reboot after the checkdisk
6) manually make the c:\wubi folder
7) manually make the c:\wubi\install folder
8) move the .iso into the c:\wubi\install folder
9) reinstall with test3
10 reboot

The process seems to be completing without any issues.  This is much farther than I have gotten at any point with any prior installer.

-Jim

P.S.  Also, I accepted all defaults in the install except for the username.  I would have liked to use a larger partition size, but I am trying to figure this out.

Follow-up:

Just posting a follow up rather than creating a separate post:

The installer appeared to complete and the computer rebooted.

I choose to select the Ubuntu menu item. 

Ubuntu appeared to start and got the point where it plays the start up sound and then where it would normally begin to present a desktop it stops.  I have the Ubuntu background and a movable cursor but it won't continue.  The HDD light periodically flashes.

The last time this happened it knocked my NTFS partition in the head and I had to remove the HDD and fix it on another computer.  Hopefully this doesn't happen here.  Last time it happened there was a long period of nothing on the HDD indicator then a lengthy HDD light (flickering once in a while but mostly active), then nothing.  After I reboot that's when I can no longer access the partition and I have to run the fix on the other computer.

BTW, this is a different notebook than the one I had problems with before, so this has now happened on two notebooks.   The similarity is that this is very close in terms of the model.  If you know much about HP/Compaq HP simply takes their own internal designs, puts a different shell on it, and then rebrands it as Compaq.  So this is effectively the same class of notebook.  Both have similar processor, memory, HDD size, prior install, etc.

This time I did an alt+ctrl+backspace which caused it to reload the desktop.  When I did this it prompted me for the username again and password except now it is sitting at a the Ubuntu background with a white box about 1/9th the total screen size without any text.  The cursor is movable.

Some more follow-up:

I did an alt+ctrl+F2 and logged in at the terminal prompt.  I then did a directory list.  It showed a couple folders.  So I then did a cd /media/host and did another directory list.  It lists the files there.  Shortly after it finished displaying the listing it dumps out a message about my broadcom wireless indicating "Error:  Microcode "bcm43xx_microcode5.fw" not available for load failed."

No this isn't a Wubi issue but the way the NTFS-3g is configured may be part of the issue and that probably is a wubi config issue.

---

### Post by tinybit on 2007-05-30
> **yapel said:**
> Well, Test 3 fails to work on my IBM Thinkpad R40 in exactly the same way as Test 2, i.e. cannot find grldr! Any quick fix?

Is this a 137G issue? I guess this machine has a disk with size less than 137G considering it is a notebook.

---

### Post by yapel on 2007-05-30
But I thought this 137G issue is for older machines which fail to read BEYOND 137G! So how would a smaller drive gets into this problem? Btw, my drive is 80GB.

---

### Post by viralbug on 2007-05-30
when i ry to download, it still downloads the Wubi-7.04-test**2** file. where is the new wubi version?

---

### Post by tinybit on 2007-05-30
There is still some problems about the NTFS boot sector code in GRLDR and GRLDR.MBR.

I think Bean123 will solve them for us. Please be patient.

---

### Post by ago on 2007-05-30
> **viralbug said:**
> when i ry to download, it still downloads the Wubi-7.04-test**2** file. where is the new wubi version?
You might have the page cached. When you see the white page, cancel the download and refresh the browser.

---

### Post by ago on 2007-05-30
> **yapel said:**
> Well, Test 3 fails to work on my IBM Thinkpad R40 in exactly the same way as Test 2, i.e. cannot find grldr! Any quick fix?

Copy grldr on all partitions

---

### Post by ago on 2007-05-30
> **jimbo99 said:**
> On my HP Pavillion zx5000 after removing the prior install and reinstalling  using a 10gig virtual disk size the system hangs after "No RAID disks".  Then it dumps a bunch of messages about:

Check root= bootarg cat /proc/cmdline
or missing modules, devices:  cat /proc/modules ls /dev
ALERT! /media/hosts/wubi/install/install.virtual.disk does not exist.  Dropping to a shell!

Then some info about busybox and then a shell prompt.

Upon looking at the c:\wubi\install the install.virtual.disk is there but it is only 100k.

I also see you created some metalink files for various Ubuntu flavors.

I'll have a look later on today. In the meantime, when you are in the shell do

ls /media/host/wubi/install

and see if you can see the virtual disk. The 100K size is ok.

---

### Post by ago on 2007-05-30
> **jimbo99 said:**
> 
1) remove the share from the c: in XP.

That might be the only point that makes a difference, the others should be irrelevant or maybe a simple reinstallation would have been sufficient anyway. PS There is no need to uninstall manually. Just run wubi again and it will give you an option to uninstall and backup the ISO.

> The last time this happened it knocked my NTFS partition in the head
Did you hardboot the last time? That can corrupt a file system. If you need to reboot the hard way see the alt+sysrq key combinations in linux.

> I did an alt+ctrl+F2 and logged in at the terminal prompt.  I then did a directory list.  It showed a couple folders.  So I then did a cd /media/host and did another directory list.  It lists the files there.  Shortly after it finished displaying the listing it dumps out a message about my broadcom wireless indicating "Error:  Microcode "bcm43xx_microcode5.fw" not available for load failed."
Use terminal 3 (ctrl+alt+f3), you can disregard the broadcom for now. Next time do not press ctrl+alt+backspace but only ctrl+alt+f3. Then you can debug by looking at the logs in /var/log or by using commands such as "ps ax". See what process is currenctly running. You can move across terminals with (ctrl+)alt+f#

---

### Post by MilchFlasche on 2007-05-30
> **ago said:**
> Copy grldr on all partitions

Hi, I've done by your suggestion, copied grldr to all my partitions and successfully installed Ubuntu.

However, the process of the installation was wholly weird. I wonder is there anything else to be copied other that the grldr file?

First, although the "No GRLDR" problem was solved, but I found that the installer didn't detect my language setting when I installed Wubi. I chose Chinese (Traditional) first  in the Wubi installer dialog, but in Ubuntu installer there was no choices corresponding to this, and I had to chose English to proceed and complete the installation.

Second, every time I boot with "Ubuntu", I got the error
```
[timestamp] hdd: error code: 0x70 sense_key:0x03 asc: 0x11 ascq 0x00
[timestamp] Buffer I/O error on device hdd - logical block 3357322
```
I've search for similar reports on the forum, but I wonder if this problem has to do with the GRLDR issue, so I mention this here too.

Third, after those hd and buffer I/O error are passed, during the booting of Ubuntu I also see (not exactly the original messages below):```

Preparing local drives to...
/media/host/wubi/disks/usr.virtual.disk No such file or ...
/media/host/wubi/disks/extra.virtual.disk No such file or ...
```

With these three major weird phenomena, my Ubuntu instance is kind of crippled now, because every package I install seems not to take effect, including language support I need, NVIDIA driver... so I stopped trying and am reporting here.

Please instruct me if anything above doesn't have to do with GRLDR issue :)

Thank you first for all the hard work!

---

### Post by ago on 2007-05-30
> **MilchFlasche said:**
> First, although the "No GRLDR" problem was solved, but I found that the installer didn't detect my language setting when I installed Wubi.
We'll look into that

> [timestamp] Buffer I/O error on device hdd - logical block 3357322[/CODE]
That might be due to a bad hard disk block

> 
Preparing local drives to...
/media/host/wubi/disks/usr.virtual.disk No such file or ...
/media/host/wubi/disks/extra.virtual.disk No such file or ...
You can ignore that

> because every package I install seems not to take effect, including language support I need, NVIDIA driver... so I stopped trying and am reporting here.
That's strange, do you have  r/w access to the filesystem?

---

### Post by samarita on 2007-05-30
[COLOR="Blue"]Hi,

I have tried to use the installer but when rebooting to continue I get a screen message stating that the username is incorrect. I cannot use the keyboard and nothing happens.

I used the installer on another computer and therre it says that some file is missing.

Not very good start for me.

Regards,[/COLOR]

---

### Post by antini on 2007-05-30
> **jimbo99 said:**
> I also see you created some metalink files for various Ubuntu flavors.

Nice to see all the progress on Wubi! I'm really glad metalink is getting used for repairable downloads.

I know Ubuntu Christian Edition would like to be included if possible. They use metalinks too and their's is at

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html)
[http://ubuntuce.ashburn.newlife4me.com/metalink/Ubuntu_7.04_i386_Christian_Edition_v3_1.iso.metalink](http://ubuntuce.ashburn.newlife4me.com/metalink/Ubuntu_7.04_i386_Christian_Edition_v3_1.iso.metalink)

---

### Post by ago on 2007-05-30
> **antini said:**
> Nice to see all the progress on Wubi! I'm really glad metalink is getting used for repairable downloads.

I know Ubuntu Christian Edition would like to be included if possible. They use metalinks too and their's is at

[http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html)
[http://ubuntuce.ashburn.newlife4me.com/metalink/Ubuntu_7.04_i386_Christian_Edition_v3_1.iso.metalink](http://ubuntuce.ashburn.newlife4me.com/metalink/Ubuntu_7.04_i386_Christian_Edition_v3_1.iso.metalink)


We'd need an alternate iso metalink

---

### Post by yapel on 2007-05-30
> **ago said:**
> Copy grldr on all partitions

But my HDD has only ONE partition! It used to have 2, but my IT removed the IBM-Service (i.e. recovery) since Day 1.

---

### Post by ago on 2007-05-30
> **samarita said:**
> 
I have tried to use the installer but when rebooting to continue I get a screen message stating that the username is incorrect. I cannot use the keyboard and nothing happens.
it might be that your keyboard was not detected properly. Press alt+ctrl+F3 and try to type something

> 
I used the installer on another computer and therre it says that some file is missing.

can you provide more details?

Also what version were you using?

---

### Post by ago on 2007-05-30
> **yapel said:**
> But my HDD has only ONE partition! It used to have 2, but my IT removed the IBM-Service (i.e. recovery) since Day 1.
do you see C:\grldr ? what's in  boot.ini?

---

### Post by MilchFlasche on 2007-05-30
> **ago said:**
> That's strange, do you have  r/w access to the filesystem?Well I forgot to offer the information that I was installing Wubi Test3 on my NTFS hard drive (actually it's quite common that people install Wubi on Win XP, and therefore on NTFS isn't it ;) ) Would this affect my r/w privilege in Ubuntu? And how should I fix this? Thank you and sorry for asking so many peripheral problems within this thread :p

---

### Post by ago on 2007-05-30
Wubi should normally access the ntfs partitions r/w and the ubuntu partition within the virtual file also r/w. If for some reason ntfs is accessed r/o then there is no way to access any file r/w in ubuntu. But if that happens it's a bug and we'd like to know about it.

---

### Post by yapel on 2007-05-30
> **ago said:**
> do you see C:\grldr ? what's in  boot.ini?

As it is my office notebook, and today is a public holiday here ( GMT+8 ), I will revert with full details tomorrow. Thanks!

---

### Post by MilchFlasche on 2007-05-30
> **ago said:**
> Wubi should normally access the ntfs partitions r/w and the ubuntu partition within the virtual file also r/w. If for some reason ntfs is accessed r/o then there is no way to access any file r/w in ubuntu. But if that happens it's a bug and we'd like to know about it.

Thank you. Do I have a way to reconfirm the access class of my Wubi to my NTFS?

By the way, I have compressed the hard drive with Windows XP built-in option, does this have to do with it?

---

### Post by ago on 2007-05-30
The general idea is that if users are very accurate in describing their problems and if we can reproduce them on our machines then we can try to fix them. If users are vague and/or we cannot reproduce the error it's much more difficult for us.

---

### Post by MilchFlasche on 2007-05-30
> **ago said:**
> The general idea is that if users are very accurate in describing their problems and if we can reproduce them on our machines then we can try to fix them. If users are vague and/or we cannot reproduce the error it's much more difficult for us.
Yeah... :p I'm so sorry. And please pardon me, because after a reboot from XP to Ubuntu, I just found that the packages I downloaded (Chinese support and NVIDIA driver) has taken effects now, and I can also log in to this forum on Ubuntu successfully (because it seems that now the system can write cookie information to the disk).

And as for the "hdd" bad block, I have removed the Ubuntu liveCD in my CD R/W machine, and the messages ceased to appear...

So actually not many problems in fact... except for the language option during installation... Sorry for all the mess and thank you for your patience ;)

Cheers!

---

### Post by Vadi on 2007-05-30
I'm installing Wubi on a toughbook cf-m34, windows 2000, ntfs file system.

For some reason, test3 isn't modifying the C:\boot.ini file to include ubuntu inside it. Is there something I can to get it modified, or could someone help me do it manually?

I'm not on the machine right now, but I'll post the file tomorrow if it's needed.

---

### Post by omgDarkWillow on 2007-05-30
Test3 crashes when I try to open it. "Wubi-7.04.... has encountered a problem and needs to close". Test2 still works, though.

---

### Post by ago on 2007-05-31
if you have boot.ini issues, can you please try: [http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by ago on 2007-05-31
> **omgDarkWillow said:**
> Test3 crashes when I try to open it. "Wubi-7.04.... has encountered a problem and needs to close". Test2 still works, though.

Run Test2, uninstall, then run Test3

---

### Post by mlentink on 2007-05-31
I downoaded test3 yesterday, installed it on my work notebook (HP Compaq nx7400) and everything works.

A few little quirks so far: I had explicitly specified the Dutch language version, yet the menu's are all still in English, even when the indiviual menu options are in Dutch.

At shut down, the system hamgs just before it would normally cut off the power. No big deal, I can manually switch it off, but it could have something to do with power management, which I have not tried yet.

---

### Post by ago on 2007-05-31
> **mlentink said:**
> A few little quirks so far: I had explicitly specified the Dutch language version, yet the menu's are all still in English, even when the indiviual menu options are in Dutch.
You need to do a system update to install all the language packs, only a few localization can fit onto the CD, the rest are installed on first update

> At shut down, the system hamgs just before it would normally cut off the power. No big deal, I can manually switch it off, but it could have something to do with power management, which I have not tried yet.
It can be that your acpi is not supported, so linux cannot send a shutdown instruction to the bios

---

### Post by Vadi on 2007-05-31
Okay, I've downloaded and installed that version. Defragmented the disk with jkdefrag before rebooting too, and ubuntu this time did come up as an option. But even before the grub starts, I get an error that windows 2000 (the os I'm using primarily on this machine) could not start, because a file in the windows root sys23\ntoskrnl.exe is missing or corrupt.

Any idea what did I mess up?

I picked the Xunubtu version by the way, left the rest as defaults. I also have 1.88gb free (out of 9.36, so nearly a quarter) space on the hdd.

---

### Post by yapel on 2007-05-31
> **ago said:**
> do you see C:\grldr ? what's in  boot.ini?

(1) C:\grldr

29-May-07   07:29 AM    176,718 bytes

(2) boot.ini

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
c:\grldr="Ubuntu"

Any further advice please?

---

### Post by Vadi on 2007-06-01
Okay, I reinstalled the latest minefield, but still came to the same problem (well the boot.ini one is fixed, this one is different).

After I reboot, and select Ubuntu, the laptop seems to freeze for a bit. Then it displays this:

Windows 2000 could not start because the following file is missing or corrupt:
<windows 2000 root>\system32\ntoskrnl.exe
Please re-install the file above.

I did a search on my computer for that file, and several come up. Three in C:\WINNT\$NtUninstall..., one in C:\WINNT\Driver Cache\I386, another in C:\WINNT\ServicePackFiles\i386, and the last one, whose name was all caps in C:\WINNT\system32. The last one's file description says that it's the "NT Kernel & System". But the trick is that the windows 2000 loads and works fine. So any idea why isn't grub getting a chance to load even?

---

### Post by tinybit on 2007-06-01
> **Vadi said:**
> well the boot.ini one is fixed

Just use this one manually.

---

### Post by miketowninc on 2007-06-02
When will the grub be fixed in the beta 4?
lol

---

### Post by ArieT on 2007-06-02
I tried this and it seems to work but during the installation my computer crashed. This because of the bad cooling system in my pc. After the crash i started my pc again but windows or even the windows bootloader won't load anymore. This isn't a real problem to me because i don't use windows anymore but for others users this might be a BIG problem. The installer may not destory windows because of a simple crash.

---

### Post by alakalaka99 on 2007-06-02
I am thinking about downloading Test3, but if i do. Can i put all my old data from Test2 and apply it into 3, im thinking you just copy and paste the drives, but i want larger drives, thats the only reason i would reinstall, so i can start out with more space. But would i have to reinstall all my other programs to do so, or could i just add my current drive stuff into the new ones? If this isnt too confusing, please reply :)

---

### Post by Vadi on 2007-06-03
What do you mean?

I'll try re-installing test3 again then I guess, but right now the minefield can't get me into grub even.

---

### Post by skezza on 2007-06-03
Test3 simply gives me an invalid username error every time i try and install. No Luck yet :(

---

### Post by jegHegy on 2007-06-04
Tested with UbuntuStudio, no problems found besides the usr.virtual.disk and extra.virtual.disk not found message at boot.

---

### Post by LegoAddict on 2007-06-04
Is this version supposed to have any fixes for the suspension/hiberation problems some people have been having?

---

### Post by jxhndxe on 2007-06-04
I've had no problems whatsoever with test3.  Then again, I didn't install Automatrix2 this time, as I did with test2 and ended up with shutdown problems.

I uninstalled Wubi and completely started from scratch...not something I want to do have to again, so what is the easiest way to maintain my Ubuntu installation while upgrading Wubi versions?

---

### Post by Vadi on 2007-06-04
No luck still.

I've installed test2, it got me into grub just fine. Froze at 33%, but that's okay, since that was a known problem there. I installed then the latest minefield - but it now gives me the same old error before even loading grub, that ntoskrnl.exe is missing or corrupt. While it's perfectly fine and win2k still boots from it, and test2 did too.

Any idea why the minefield is failing to load it then?

---

### Post by ago on 2007-06-04
Use test 3

---

### Post by Vadi on 2007-06-04
Test3 was the one that wasn't modifying the boot.ini properly, but I'll try it once more. I'll save a copy of the current working boot.ini just in case.

Edit: Installed test3, it didn't modify the boot.ini like it was previously, so I copied over the working one from the minefield. Waiting on the thing to defrag, and then I'll reboot

---

### Post by Vadi on 2007-06-05
Test3 gives me the ntoskrnl.exe before grub also :/. Looks like something happened to it since test2.

---

### Post by Saltire59 on 2007-06-05
Installed using test3 and had no problems. Previously I was stuck at 33%.:D

---

### Post by viralbug on 2007-06-06
> **skezza said:**
> Test3 simply gives me an invalid username error every time i try and install. No Luck yet :(

im having the same problem here. it gives an invalid username error. :(

---

### Post by ago on 2007-06-06
> **viralbug said:**
> im having the same problem here. it gives an invalid username error. :(

Is this when installing or when loggin in (blue/red text-mode screen or orange screen?)

---

### Post by viralbug on 2007-06-06
^^ it gives me an error while installing. ive tried different usernames but it still gives the same error. i pressed ESC to bring up the menu and i continued with the installation. it installed perfectly and even booted to the ubuntu login screen, but it gave a username error there too.

---

### Post by ago on 2007-06-06
> **viralbug said:**
> ^^ it gives me an error while installing. ive tried different usernames but it still gives the same error. i pressed ESC to bring up the menu and i continued with the installation. it installed perfectly and even booted to the ubuntu login screen, but it gave a username error there too.

Run wubi again then attach here your preseed.cfg (use "ubuntu" as password)

---

### Post by viralbug on 2007-06-06
i suppose this is what you need? i used ubu as the username.

d-i passwd/root-login boolean false
d-i passwd/user-fullname string ubu User
d-i passwd/username string ubu
d-i passwd/user-password-crypted password $1$xgp9bbPL$gkfS64wzGvxl57XdbizAv0

---

### Post by ago on 2007-06-06
I'd prefer the full file you can zip it and attach to your post here

---

### Post by viralbug on 2007-06-06
heres the file
[preseed]("http://rapidshare.com/files/35632772/preseed.zip")

---

### Post by ago on 2007-06-06
the link does not work for me. when you create a new post here there is a "Manage Attachment" button. You can use that

---

### Post by viralbug on 2007-06-06
oops sorry about that. heres the file.

---

### Post by ago on 2007-06-06
thanks going to test it soon

---

### Post by ago on 2007-06-06
hmmm your preseed works fine for me... I am installaing the base system right now and was not prompted anything

---

### Post by viralbug on 2007-06-07
i tried installing test2 and strangely it didnt give any error. earlier it used get stuck at 33% but now it worked and didnt give the username error too. but somehow the system shut down in between the installation so couldnt complete it. will try it again.
also the installation takes too much of time for me. normally it should take around 45mins-1hr but it takes a few hours for me.

---

### Post by ago on 2007-06-07
Please use test3 or the latest minefield.

---

### Post by Rohen on 2007-06-08
Hello all this is my firt post.

I just wanted to quickly say that I'm thankful there are people out there that are willing to create new things for people who have no idea about this kind of technical stuff.  THANKS :D

I installed TEST2, and ran into the 33% problem.  Then I looked for help at the forums and ran into a thread, that lead me into this post.  I installed TEST3 without any problems at all.  Now I'm a happy user of Ubuntu and I will, once I get around to it, make a full conversion into UBUNTU.

I DO have one question though:  I run a intel TOSHIBA labtop 256 RAM, 1.8 Ghz.  Disk access is REALLLLY slow, and I mean: I log in, click on the firefox icon on the top left, and 3-4 min later it actually opens.

It's the same for any other application, specially OpenOffice, that takes like 10 min.  Is this normal with my current system specs and Wubi?  Any feedback is welcome.

And once again, AGO: you da man my friend!  Thanks. :popcorn:

---

### Post by ago on 2007-06-08
> **Rohen said:**
> I DO have one question though:  I run a intel TOSHIBA labtop 256 RAM, 1.8 Ghz.  Disk access is REALLLLY slow, and I mean: I log in, click on the firefox icon on the top left, and 3-4 min later it actually opens.

There are generally 3 reasons for that:

* you are using swap a lot (that would really slow you down)
* you have a very fragmented HD
* we miss the driver that your machine may need (see the wubiguide on how to check DMA).

You can check the resource utilization with the system monitor to see if there is anything that takes abnormal resources. With your specs you might want to try Xubuntu.

How long did it take to do the installation? I am talking about the one with blue screens.

PS: wubi is the product of many people, not just me.

---

### Post by Rohen on 2007-06-08
Gotcha, but you get my meaning.  Gotta include the group!  But out of curiosity how many people contributed?

And to be honest, I have no idea how long the installation took.  I left the computer running and went out for a bit.  I'll check with those tips and get back to you.  Thanks.

---

### Post by ago on 2007-06-08
[http://cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html#credits](http://cutlersoftware.com/ubuntusetup/wubi/en-US/faq.html#credits)

---

### Post by Rohen on 2007-06-09
Ok, 

So I ran **Jkdefrag**.  Because I had already set the virtual disk smaller than 4GB, I assumed I didn't have to Uninstall and re-install.

Then I tried checking if my HD is running at full speed so I *Shift+F2 hdparm -I /dev/sda*.  Nothing happened.  I tried with:*/dev/sda, /dev/hda, /dev/sdb, /dev/hdb*.  Still nothing happened.

So does this mean my HD isn't included?

_**SPECS**_
HD: ATA 
Model: IC25N030ATCS04-4
Firware: SCSI
Filesystem: NTFS

As I'm writing this, the Labtop is using **150 RAM** and **111 SWAP**.  That's a lot of SWAP right?!  I only have Firefox and Thunderbird open.  If that's the case I'll prob switch to my VAIO...  

THANKS!

---

