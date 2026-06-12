---
title: "GRUB Error 15 on NTFS (2nd menu.lst)"
date: 2008-03-10
forum: General Help
---

### Post by cranphin on 2008-03-10
Hi!

I'm trying to get wubi to run (alpha 8.04).
Grub loads from the c: drive (which is fat), but then fails to load the menu.lst on the install drive (k:, which is ntfs).
I get a  Error 15, File not found.

I'm not an entire noob, so I've tried in grub:
'root (hd0,<TAB>', which gives me a list of possible partitions.
Now all but my c: drive are NTFS.
But in the list, some show as "is ntfs", and some show as "unknown".
They all are shown as type '0x7'.

After investigating more, I did find one difference between partitions that can be loaded, and that can be loaded:
The partitions that don't load, have sector size 16.
The partitions that do load, have sector size 8.
So, could this be the cause of grub failing, sector size 16 on ntfs ?
The partitions are not compressed, and have been checked for errors.

I also tried the fstest.exe from this thread:
[http://ubuntuforums.org/showthread.php?p=2763149#post2763149](http://ubuntuforums.org/showthread.php?p=2763149#post2763149)

Note, my partition letters are a bit spaced, but are in order of partition number. These are all NTFS.
E,F,K have 16 sectors per cluster, the rest 8 per cluster.


Output:

K:\fstest>fstest.exe info d:
part_base: 0x3F3EC1 (2023M)
part_leng: 0x42EFB92 (34271M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000

K:\fstest>fstest.exe info e:
ntfs_mount: 0

K:\fstest>fstest.exe info f:
ntfs_mount: 0

K:\fstest>fstest.exe info k:
ntfs_mount: 0

K:\fstest>fstest.exe info l:
part_base: 0x162919E6 (181539M)
part_leng: 0xC35314E (100006M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000
Warning: reading beyond the 137G limit

K:\fstest>fstest.exe info m:
part_base: 0x225E4B73 (281545M)
part_leng: 0xC35314E (100006M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000
Warning: reading beyond the 137G limit

---

### Post by ago on 2008-03-10
Hi cranphin, thanks for the detailed report, wish I had more like that...
I am no grub4dos expert so I will ask grub4dos devs to have a look at the above.

---

### Post by cranphin on 2008-03-11
> **ago said:**
> Hi cranphin, thanks for the detailed report, wish I had more like that...
I am no grub4dos expert so I will ask grub4dos devs to have a look at the above.

My pleasure, I'm a programmer myself, so I know the value of detail ;)
Let me know if I can provide any more information :)

Note I'm just guessing the sector size is the problem, it seems to match the situation here, but that's not guarantee.

---

### Post by bean123 on 2008-03-11
Yes, the driver assume maximum cluster size of 4096 bytes (8 sector). btw, how do you know the sector size for your partition ?

---

### Post by ago on 2008-03-11
Thanks bean123 for looking into this ;)

---

### Post by bean123 on 2008-03-11
please try the new version of fstest.exe, see if it can list and compare files in your previous unknown partition.

---

### Post by ago on 2008-03-11
Bean123 is it possible/reasonable to change that and recompile?

---

### Post by bean123 on 2008-03-11
> **ago said:**
> Bean123 is it possible/reasonable to change that and recompile?

if the cluster size is the only reason that cause this problem, i think it's easy to fix.

---

### Post by ago on 2008-03-11
Would it also be possible to allow 2048 chars as kernel commandline length?
Not sure if it is because grub4dos but I get truncated commandline (which does not seem to be the case when using grub).

---

### Post by bean123 on 2008-03-11
> **ago said:**
> Would it also be possible to allow 2048 chars as kernel commandline length?
Not sure if it is because grub4dos but I get truncated commandline (which does not seem to be the case when using grub).

The maximum command line length is 1600, it's caused by an implementation limitation of grub legacy.

---

### Post by cranphin on 2008-03-11
Firstly, how I know, Paragon Partition Manager 7.0:
A '16 sectors' drive K:
[IMG]http://tursiops.org/crandonkphin/KDrive.JPG[/IMG]

A '8 sectors' drive L:
[IMG]http://tursiops.org/crandonkphin/LDrive.JPG[/IMG]

---

### Post by cranphin on 2008-03-11
Secondly:

> **bean123 said:**
> please try the new version of fstest.exe, see if it can list and compare files in your previous unknown partition.

K:\fstest>fstest2.exe info k:
version: 1.0 build 2
part_base: 0x941F103 (75838M)
part_leng: 0xCE728A4 (105701M)

blocksize: 512
spc: 16
mft_size: 2
idx_size: 8
mft_start: 0x600000

K:\fstest>fstest2.exe info l:
version: 1.0 build 2
part_base: 0x162919E6 (181539M)
part_leng: 0xC35314E (100006M)

blocksize: 512
spc: 8
mft_size: 2
idx_size: 8
mft_start: 0x600000
Warning: reading beyond the 137G limit

Looks a lot better to me! :D
Listing seems to work fine too now (with fstest.exe list!)

---

### Post by ago on 2008-03-11
> **bean123 said:**
> The maximum command line length is 1600, it's caused by an implementation limitation of grub legacy.

Hmmm in my case it gets truncated way before that, closer to 256 on top of my head

---

### Post by ago on 2008-03-11
1600 would be more than adequate

---

### Post by ago on 2008-03-11
Bean123 would it be possible to upload any change to svn? Current wubi build scripts use that to sync with grub4dos and it would make it easier for other devs to be on the same page.

Bunch of thanks in advance!

---

### Post by bean123 on 2008-03-11
> **ago said:**
> Hmmm in my case it gets truncated way before that, closer to 256 on top of my head

thanks for the tip, i can look into this sometime.

> would it be possible to upload any change to svn? Current wubi build scripts use that to sync with grub4dos and it would make it easier for other devs to be on the same page.

normally i would prefer to build a test version first, just in case some other problem shows up, this would avoid committing too many version to the svn.

---

### Post by bean123 on 2008-03-11
cranphin, please try this new version of grldr, it accepts maximum spc of 16.

---

### Post by ago on 2008-03-11
> **bean123 said:**
> normally i would prefer to build a test version first, just in case some other problem shows up, this would avoid committing too many version to the svn.

I appreciate that, was mentioning that because the end of this week it is beta freeze across ubuntuland, and while I would not expect to have too much trouble justifying an exception for a relevant bugfix it would be preferrable to merge in any required exception before that (the burden is on my side of course).

---

### Post by bean123 on 2008-03-11
> **ago said:**
> I appreciate that, was mentioning that because the end of this week it is beta freeze across ubuntuland, and while I would not expect to have too much trouble justifying an exception for a relevant bugfix it would be preferrable to merge in any required exception before that (the burden is on my side of course).

ok, i'd try to speed things up a little bit, :)

---

### Post by ago on 2008-03-11
much appreciated!!! :D

---

### Post by cranphin on 2008-03-11
> **bean123 said:**
> cranphin, please try this new version of grldr, it accepts maximum spc of 16.

It loads and gives me access to all my partitions, Hurray :D

Renamed it to wubildr so it'd get loaded (is that specific to 8.04?).

Need to figure out how to make it load linux now (it drops me in grub menu and sits there, but with the root (hd0,... stuff I can see all my partitions, and all files on all partitions :) ). I guess the wubildr is slightly differently configured or so, dunno, something to figure out tomorrow ^_^

But it does work, yay :)

---

### Post by cranphin on 2008-03-11
I never sleep when I'm trying to install linux XD

Right:
Moved the new grldr to c:\wubildr
Copied K:\ubuntu\winboot\menu.lst to c:\menu.lst
Reboot:
- grldr(wubildr) seems to load.
- it picks up c:\menu.lst
- it seems to load K:\ubuntu\install\boot\grub\menu.lst
I get the error:
Error 13: Invalid or unsupported executable.

Above it some info of I think the config line, which includes the kernel /ubuntu/install/boot/vmlinuz. I guess it is failing to load that ?

Any hints ? :)

---

### Post by ago on 2008-03-11
> **cranphin said:**
> It loads and gives me access to all my partitions, Hurray :D

Renamed it to wubildr so it'd get loaded (is that specific to 8.04?).

Need to figure out how to make it load linux now (it drops me in grub menu and sits there, but with the root (hd0,... stuff I can see all my partitions, and all files on all partitions :) ). I guess the wubildr is slightly differently configured or so, dunno, something to figure out tomorrow ^_^

But it does work, yay :)

Great news! I'll wait for Bean123 svn update then I will merge it in!

Wubildr has a different built-in menu.lst than grldr. You can see the menu.lst in /ubuntu/winboot/menu.lst. Copying that to the root folder should be enough! I am not sure why you have an error.

You can also try to run it manaually from grub shell:

configfile /ubuntu/install/boot/grub/menu.lst

or enter directly the commands as you see them in the first item in /ubuntu/install/boot/grub/menu.lst

---

### Post by cranphin on 2008-03-12
> **ago said:**
> Great news! I'll wait for Bean123 svn update then I will merge it in!

Wubildr has a different built-in menu.lst than grldr. You can see the menu.lst in /ubuntu/winboot/menu.lst. Copying that to the root folder should be enough! I am not sure why you have an error.

You can also try to run it manaually from grub shell:

configfile /ubuntu/install/boot/grub/menu.lst

or enter directly the commands as you see them in the first item in /ubuntu/install/boot/grub/menu.lst

I noticed the different menu.lst, if you open grldr/wubildr in wordpad you can actually see it at the end of the file :D

the one in grldr looks for /menu.lst, so I figured that putting a file in c:/ would work, and it does.
I copied the file from K:\ubuntu\winboot\menu.lstt, cause that looks pretty much identical to the one built into wubildr, and that also worked, cause it then tries to load  /ubuntu/install/boot/grub/menu.lst, which I'm sure it finds and loads from the k: drive.
But then executing /ubuntu/install/boot/grub/menu.lst I get the error 13.

But, I'll look more into that today after work :)
Mayby it needs a good defragging.
And mayby I can test somethign with that fstest.exe, the comp option, what does that? can I compare a file read from hd directly with a file read via the ntfs loader? then I could see if that goes properly :)

Note to self: 
    13 : Invalid or unsupported executable format
        This error is returned if the kernel image being loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

Note to self 2:
[http://ubuntuforums.org/showpost.php?p=2671002&postcount=53](http://ubuntuforums.org/showpost.php?p=2671002&postcount=53)
OH, just realized, the comp option is smart enough that you only need to specify the file once :D I though you had to specify two filepaths ^.^

---

### Post by cranphin on 2008-03-12
Hmm..

K:\fstest>fstest2.exe comp k:\ubuntu\install\boot\vmlinuz
File size : 1909240
Comparing .
Succeed
Warning: reading beyond the 137G limit

That looks ok to me :)

In grub after reboot:
cat --hex --length=64 /ubuntu/install/boot/vmlinuz,
first bytes look like:
DC DD 6A A5  8A B0 AC 8B
6D 98 39 F1  68 A8 6D 0B

Checking in windows wiht hex edit shows the same, so that looks correct too.

Yet, I still get the error 13, also when I just manually do kernel /ubuntu/install/boot/vmlinuz in grub.

Sooo:
Either grub is mistakingly saying my kernel is bad.
Or, my kernel is bad :)
Or, something else weird is going on ^_^

PS:
vmlinuz is identical (md5 check, hex editor), to the vmlinuz in G:\casper, when I mount K:\ubuntu\install\hardy-desktop-i386.iso in windows

PS2:
I was wondering where the iso came from, ubuntu-desktop-i386.iso.metalink suggests [http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.iso).
Which I guess would be a daily build.
I downloaded the file in multiple parts I think tho (by starting wubi installer, letting it run for a while, hit cancel when I needed to go to bed, start wubi the next day, where it seemed to continue instead of restart).
So mayby I botched the iso that way :D
Or, I just got unlucky with a bad kernel in the daily build ?
I'll just uninstall, and reinstall, gettin gthe image in one go, see if that helps ^_^

PS3:
Just for completeness, in case someone didn't realize this yet, I wanted to try 8.04 alpha ubuntu, so I'm using the 'Wubi-8.04-alpha-rev431.exe' installer :)

---

### Post by ago on 2008-03-12
I'd suggest using the latest Wubi from [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)
With the latest daily-live ISO

not that it explains the error 13...

---

### Post by bean123 on 2008-03-13
if it still don't work, you can copy vmlinuz to a fat partition and see if you can boot from it. also, you can use cmp command (in grub console) to compare vmlinuz in ntfs and fat partition.

---

### Post by cranphin on 2008-03-13
Did a clean reinstall, now vmlinuz got booted :D
Ubuntu started and installed ^.^

And then on the next boot it failed with another error XD

Thisone is a Error 15, file not found, while trying to load /ubuntu/install/boot/grub/menu.lst I think.

It seems tho that when ubuntu installed, the /ubuntu/install/boot/grub/menu.lst got removed, and a new menu.lst got written in /ubuntu/disks/boot/grub/menu.lst
I assume that is normal part of installation ? the install menu.lst is removed, and a boot linux one is written ?

I'm guessing what happens now is that it first tries to load /ubuntu/disks/boot/grub/menu.lst, but it fails on that somehow.
And then it tries to load /ubuntu/install/boot/grub/menu.lst, which no longer exists so there it bails with a error 15.

I don't know why /ubuntu/disks/boot/grub/menu.lst cannot be loaded.
I havent' had time to mess about in grub with that file.
But I have tested with fstest.exe comp (the last version) and it gives a strange error about "Non-resident attribute list too large" on the file or so.
I'll get a exact message with it when I get back home today, and see
what grub itself can tell me.
Could that be related to sector size again or so ?

Nearly there! ^_^
I kinda expect that putting the menu.lst on c: (fat) would allow me to boot linux, but I'd like to figure out while this file is not loading (while other files on k: did/do load well now, the install menu.lst and the kernel).

Hmm:
[http://svn.gna.org/viewcvs/grub4dos/trunk/stage2/fsys_ntfs.c?rev=55&view=markup](http://svn.gna.org/viewcvs/grub4dos/trunk/stage2/fsys_ntfs.c?rev=55&view=markup)
        if (valueat(pa,0x28,unsigned long)>4096)
            {
              dbg_printf("Non-resident attribute list too large\n");
              return NULL;
            }
That's a check on 4K, a 8 sector cluster is 4K right?
So should this check be based on the cluster size?

Note to self:
[http://ubuntuforums.org/showpost.php?p=2671836&postcount=54](http://ubuntuforums.org/showpost.php?p=2671836&postcount=54)

---

### Post by ago on 2008-03-13
> **cranphin said:**
> 
Thisone is a Error 15, file not found, while trying to load /ubuntu/install/boot/grub/menu.lst I think.

It seems tho that when ubuntu installed, the /ubuntu/install/boot/grub/menu.lst got removed, and a new menu.lst got written in /ubuntu/disks/boot/grub/menu.lst
I assume that is normal part of installation ? the install menu.lst is removed, and a boot linux one is written ?
Correct after installation the system boots off /ubuntu/disks/boot/grub/menu.lst
Basically the menu.lst embedded into wubildr looks first for the post-install bootloader and then falls back onto the installation one (which is removed for extra precaution).

> I don't know why /ubuntu/disks/boot/grub/menu.lst cannot be loaded.
Yeah that would be interesting. 

> But I have tested with fstest.exe comp (the last version) and it gives a strange error about "Non-resident attribute list too large" on the file or so.
Hmm another one for bean123!

> Hmm:
[http://svn.gna.org/viewcvs/grub4dos/trunk/stage2/fsys_ntfs.c?rev=55&view=markup](http://svn.gna.org/viewcvs/grub4dos/trunk/stage2/fsys_ntfs.c?rev=55&view=markup)
        if (valueat(pa,0x28,unsigned long)>4096)
            {
              dbg_printf("Non-resident attribute list too large\n");
              return NULL;
            }
That's a check on 4K, a 8 sector cluster is 4K right?
So should this check be based on the cluster size?

Seems plausible will ask bean123 to have a look at it! 
Great work! Thanks a bunch

---

### Post by bean123 on 2008-03-13
Please try the new fstest.exe

---

### Post by cranphin on 2008-03-13
> **bean123 said:**
> Please try the new fstest.exe

K:\fstest>fstest3.exe comp "k:\ubuntu\disks\boot\grub\menu.lst"
File size : 4698
Comparing
Succeed

Works! ^_^

And this is what the previous version said:
K:\fstest>fstest2.exe comp "k:\ubuntu\disks\boot\grub\menu.lst"
Non-resident attribute list too large
No $INDEX_ROOT
ntfs_dir: 18

---

### Post by ago on 2008-03-13
Bean good stuff (as usual), pls let me know when the svn is up to date.

---

### Post by bean123 on 2008-03-13
The new grldr incorporate the latest ntfs patch, please test. It also increase the command line length to 1024 bytes. ago, would you please verify it ?

About the svn commit, tinybit says there is still some problem to fix, maybe just wait a day or two. what's the dead line of the code freeze ?

---

### Post by ago on 2008-03-13
Thanks bean will try that tonight!
Unfortunately the beta freeze is today!
Not a huge deal it mostly means more paperwork for me!

It is important though not to miss the beta, that provides a LOT of good feedback!

---

### Post by cranphin on 2008-03-13
> **bean123 said:**
> The new grldr incorporate the latest ntfs patch, please test. It also increase the command line length to 1024 bytes. ago, would you please verify it ?

About the svn commit, tinybit says there is still some problem to fix, maybe just wait a day or two. what's the dead line of the code freeze ?

It works! :D
Posting from Ubuntu Hardy Heron booted of my freaky 16 sector NTFS partition ^.^

---

### Post by ago on 2008-03-13
While you are there, can you pls test suspend and hibernation?

For hibernation you will first have to swapoff -a, then generate a large enough swap file with dd, then swapon. Suspend is expected to work, hibernation is not.

Note that there were problems today with glibc so even though a fix was on its way, upgrades are not recommended today.

---

### Post by cranphin on 2008-03-13
Sorry but I've got a very pleasurable weekend planned, and need to attend to preparing for it now, won't be able to assist till monday I'm affraid ^.^

---

### Post by ago on 2008-03-13
you have already done a lot! thanks!
monday is good by the way...

---

### Post by ago on 2008-03-13
> **bean123 said:**
> The new grldr incorporate the latest ntfs patch, please test. It also increase the command line length to 1024 bytes. ago, would you please verify it ?


Bean123 works well here! 
I did not test sector size 16, but I can boot fine, and commandline truncation is fixed!
Good work!

---

### Post by bean123 on 2008-03-14
ok, it's committed.

btw, the new grldr.mbr is over 8192 bytes, it doesn't work in boot.ini anymore. If you want the old grldr.mbr, just use the first 8192 bytes of grldr, or grldr.mbr from grubinst.

---

### Post by ago on 2008-03-14
> **bean123 said:**
> ok, it's committed.
Thanks, will upload tonight

> btw, the new grldr.mbr is over 8192 bytes, it doesn't work in boot.ini anymore. If you want the old grldr.mbr, just use the first 8192 bytes of grldr, or grldr.mbr from grubinst.
ok will check that. Any reason for such a large grldr.mbr?
At the moment I get grldr.mbr off stage2/grldr.mbr

---

### Post by bean123 on 2008-03-14
> **ago said:**
> Thanks, will upload tonight


ok will check that. Any reason for such a large grldr.mbr?
At the moment I get grldr.mbr off stage2/grldr.mbr

tinybit add code to detect chs geometry of legacy disk, which causes grldr.mbr to grow over 8192. windows nt/2k/xp only load the first 8192 bytes of boot file, so it will have problem.

---

### Post by ago on 2008-03-15
I have uploaded rev453 including the new grub4dos, please test it out! Particularly if you have XP.

Bean123, the command to generate wubildr/wubildr.mbr is the following. Could you please doublecheck that and the wubildr.mbr embedded in wubi-rev453? ([http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)) 

```

wubildr:
	mkdir -p $(winboot_dir)
	cp data/menu.winboot $(winboot_dir)/menu.lst
	cd src/grub4dos/trunk; ./configure --enable-preset-menu=$(winboot_dir)/menu.lst
	cd src/grub4dos/trunk; make
	cd src/grubutil/trunk/grubinst; make
	mv -f src/grub4dos/trunk/stage2/grldr $(winboot_dir)/wubildr
	dd if=$(winboot_dir)/wubildr of=$(winboot_dir)/wubildr.mbr bs=1 count=8192
	mv -f src/grub4dos/trunk/stage2/grub.exe $(winboot_dir)/wubildr.exe
	cd $(winboot_dir); ../../src/grubutil/trunk/grubinst/grubinst -o -b=wubildr wubildr.mbr

```

---

### Post by cranphin on 2008-03-19
> **ago said:**
> While you are there, can you pls test suspend and hibernation?

For hibernation you will first have to swapoff -a, then generate a large enough swap file with dd, then swapon. Suspend is expected to work, hibernation is not.

Note that there were problems today with glibc so even though a fix was on its way, upgrades are not recommended today.

Both suspend and hibernate fail (and make me have to reboot), but I wouldn't be surprised if (some of) my hardware just doesn't want to do 'm, I've never had it working properly :)

---

### Post by ago on 2008-03-19
New beta live cd will not have the above patch :(
But it will be available on the mainfield and later on as main download on wubi-installer.org

---

### Post by cranphin on 2008-03-19
> **ago said:**
> New beta live cd will not have the above patch :(
But it will be available on the mainfield and later on as main download on wubi-installer.org

Will it make it to final/rc's ?
It would seem a bit silly to have lacking ntfs support on it :)

---

### Post by ago on 2008-03-19
> **cranphin said:**
> Will it make it to final/rc's ?
It would seem a bit silly to have lacking ntfs support on it :)

Yes

---

### Post by ago on 2008-03-26
cranphin 

Can you please try rev457 available off the main page of wubi-installer.org?

---

### Post by swargy on 2008-06-20
Hi

Installed Ubuntu through windows. The install runs normally and asks for reboot. When reboot I choose Kubuntu (i chosen this last time but the prob remain with ubuntu too) and than an error pops up. 

file --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst error 
15:File not found

and than a list of paths to choose and each one leads to the same prob. 

I read above and i saw that i have 2 menu.lst.
1 in c:\ubuntu\winboot\menu.lst
and 1 in c:\ubuntu\install\boot\grub\menu.lst
I tried to edit menu.lst but there is no (hdX,Y) in there.
The c:\ubuntu\install\boot\grub\menu.lst contains the list of paths i take after boot. 


Any1 can help please ?

---

### Post by ago on 2008-06-20
[https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742](https://wiki.ubuntu.com/WubiGuide#head-7e4c85ef744a4fd4bae6766a5e6abc67f608d742)

---

### Post by swargy on 2008-06-20
Thanks Ago.

---

